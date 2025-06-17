Vagrant.configure("2") do |config|
  config.vm.provider "vmware_workstation" do |vmware|
    vmware.vmx["memsize"] = "4096"        # Memory (in MB)
    vmware.vmx["numvcpus"] = "1"          # Number of CPU cores
    vmware.vmx["ethernet0.connectionType"] = "nat" # Network type
	  vmware.vmx["virtualHW.version"] = "17"
  end

  config.vm.provision :shell, privileged: true, inline: $install_common_tools

  config.vm.define :nginx do |nginx|
    nginx.vm.box = "ubuntu/jammy64"
    nginx.vm.hostname = "master"
    nginx.vm.network :private_network, ip: "192.168.56.0"
    nginx.vm.provision :shell, privileged: true, inline: $provision_nginx
  end

  %w{application1 application2}.each_with_index do |name, i|
    config.vm.define name do |application|
      application.vm.box = "ubuntu/jammy64"
      application.vm.hostname = name
      application.vm.network :private_network, ip: "192.168.56.#{i + 61}"
      application.vm.provision :shell, privileged: false, inline: $provision_docker
    end
  end

  config.vm.provision "shell", inline: $install_multicast
end

$install_common_tools = <<-SCRIPT
apt-get -qq update
apt-get -qq install -y docker.io apt-transport-https curl
usermod -aG docker vagrant
SCRIPT

$provision_docker = <<-SHELL
sudo systemctl start docker
sudo systemctl enable docker
mkdir actions-runner && cd actions-runner
curl -o actions-runner-linux-x64-2.320.0.tar.gz -L https://github.com/actions/runner/releases/download/v2.320.0/actions-runner-linux-x64-2.320.0.tar.gz
tar xzf ./actions-runner-linux-x64-2.320.0.tar.gz
./config.sh --url https://github.com/imanyauma/ntx-devops-test --token AEE43AIMSLSA7KSZK45SS73HIQYSA
./run.sh &
SHELL

$provision_nginx = <<-SHELL
apt-get install -y nginx
systemctl start nginx
cat <<EOL > /etc/nginx/conf.d/load_balancer.conf
upstream backend_servers {
    server 192.168.74.61:3000;
    server 192.168.74.62:3000;
}

server {
    listen 80;

    location / {
        proxy_pass http://backend_servers;
        proxy_set_header Host \\$host;
        proxy_set_header X-Real-IP \\$remote_addr;
        proxy_set_header X-Forwarded-For \\$proxy_add_x_forwarded_for;
    }
}
EOL
sed -i 's|include /etc/nginx/sites-|#include /etc/nginx/sites-|g' /etc/nginx/nginx.conf
SHELL

$install_multicast = <<-SHELL
apt-get -qq install -y avahi-daemon libnss-mdns
SHELL
