# DevOps Engineer - Technical Test

Welcome to the DevOps Engineer Technical Test! This exercise assesses your ability to create automated infrastructure and CI/CD pipelines while adhering to modern DevOps methodologies.

---

## Objective

Your task is to create a CI build pipeline that deploys this Node.js web application to a load-balanced environment. You can complete this test locally using tools like Docker or on a cloud provider of your choice. If using a cloud provider, we recommend using a free-tier account to avoid costs.

---

## Requirements

### CI Build Pipeline

1. **Trigger Mechanism**:  
   - The CI job should trigger automatically when a feature branch is pushed to GitHub.  
   - If working locally, implement an alternative method to trigger the pipeline.

2. **Deployment Workflow**:  
   - The CI pipeline should deploy the application to the target environment after a successful build.

---

### Target Environment

The environment must meet the following specifications:

1. **Load Balancer**:
   - Accessible via HTTP on port 80.
   - Configured to use a **round-robin** strategy to distribute traffic between application servers.

2. **Application Servers**:
   - Two instances running this web application.
   - Each accessible via HTTP on port 3000.
   - The application must respond with:  
     `Hi there! I'm being served from {hostname}!`

---

## Tools and Technologies

You are free to use any tools and services to implement your solution. Feel free to tailor what you need Below are some options:

- **CI Services**: GitHub Actions, Jenkins, GitLab CI/CD, CircleCI
- **Provisioning Tools**: Terraform, Ansible, CloudFormation
- **Local Environment**: Docker, Vagrant, Minikube
- **Cloud Providers**: AWS, Azure, GCP
- **Load Balancers**: NGINX, HAProxy, Cloud-native load balancers
- **Version Control**: GitHub (fork this repository)

---

## Submission Instructions

1. Fork this repository to your GitHub account.
2. Implement the solution, ensuring to:
   - Commit frequently to demonstrate your development process.
   - Include a clear and structured project layout.
3. Push your final solution to your public repository.
4. Write your Solution and Execution Plan on .md file
4. Send us the URL to your repository for review.

---

## Evaluation Criteria

We will evaluate your submission based on the following:

1. **Functionality**: Does the environment meet the requirements (load balancer, two app servers, correct response)?
2. **Automation**: Is the infrastructure fully automated and deployable using IaC and CI/CD pipelines?
3. **Code Quality**: Is the code readable, modular, and maintainable?
4. **DevOps Practices**: Does the solution adhere to DevOps principles such as scalability and fault tolerance?

---

## Running the Web Application

This is a Node.js application. Use the following commands to run it locally:

- **Run Tests**:  
  ```bash
  npm test
  ```
- **Start the HTTP Server**:  
  ```bash
  npm start
  ```

---

## Notes

- Be sure to document your solution thoroughly, including:
  - How to deploy the environment.
  - Explanation of tools and services used.
  - Assumptions and challenges encountered during implementation.
- You are encouraged to showcase additional skills or optimizations (e.g., scaling, monitoring, or securing the application).

Good luck, and happy coding! 🚀

--- 

Let me know if you need further information.
