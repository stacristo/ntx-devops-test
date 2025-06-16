pipeline {
    agent any

    tools {nodejs}
    
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
		sh 'npm test'
            }
        }
    }
}


