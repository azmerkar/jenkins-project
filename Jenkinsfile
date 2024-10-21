pipeline {
    agent any
    environment{
      SERVER_CREDS = credentials('server-creds')
        
    } 
    stages {

        stage('Setup') {
            steps {
                echo "MY CREDS: ${SERVER_CREDS}"
                echo "USERNAME: ${SERVER_CREDS_USR}"
                echo "PASSWORD: ${SERVER_CREDS_PSW}"
                sh  "pip install -r requirements.txt"  
            }
        }
        stage('Test') {
            steps {
                sh '/var/lib/jenkins/.local/bin/pytest'
                
             } 
            }
        }
    
}
