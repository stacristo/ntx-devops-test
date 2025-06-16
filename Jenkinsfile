pipeline {
    agent any

    tools {nodejs "nodejs latest"}

    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
		sh 'npm test'
            }
        }
    }
}


