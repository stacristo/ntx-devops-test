pipeline {
    agent {dockerfile true}

    tools {nodejs 'recent node'}
    
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}


