pipeline {
    agent {any}

    tools {nodejs 'null'}
    
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
		sh 'npm test'
            }
        }
    }
}


