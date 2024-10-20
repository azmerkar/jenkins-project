pipeline {
    agent any
    environment {
       SERVER_CREDS = credentials('server-creds') 
    }
    stages {

        stage('Setup') {
            steps {
                echo "my creds: ${SERVER_CREDS} "
                echo "Username: ${SERVER_CREDS_USR} "
                echo "Username: ${SERVER_CREDS_PSW} "
                sh  "pip install -r requirements.txt"  
            }
        }
        stage('Test') {
            steps {
                echo "${env.JENKINS_URL}"
                echo "The DB IP username ${USERNAME} and password ${PASSWORD}"
                sh '/var/lib/jenkins/.local/bin/pytest'
                
             } 
            }
        }
    
}
