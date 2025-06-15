pipeline {
    agent {dockerfile true}

    tools {nodejs 'latest nodejs'}
    
    stages {
        stage('Build') { 
            steps {
	    	sh 'node --version'
                sh 'npm install'
		sh 'npm test'
            }
        }
    }
}


