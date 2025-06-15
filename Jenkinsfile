pipeline {
    agent {dockerfile true}

    tools {nodejs 'latest nodejs'}
    
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}


