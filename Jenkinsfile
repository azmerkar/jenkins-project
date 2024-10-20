pipeline {
    agent any
    environment {
        // IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
        // IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
        // KUBECONFIG = credentials('kubeconfig-credentials-id')
        DB_HOST = '192.168.12.1'
        USERNAME = 'user1'
        PASSWORD = 'password123'
    }
    stages {

        stage('Setup') {
            steps {
                sh  "pip install -r requirements.txt"  
                echo "The Database  IP is ${DB_HOST} "
            }
        }
        stage('Test') {
            steps {
                echo "The DB IP username ${USERNAME} and password ${PASSWORD}"
                sh 'whoami'
                sh '/var/lib/jenkins/.local/bin/pytest'
                
             } 
            }
        }
    
}
