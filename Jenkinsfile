pipeline {
    agent any

    environment {
       SERVER_CREDS = credentials('server-creds') 
        
    }

     environment {
         DB_HOST = '192.143.06.06'
         USERNAME = 'user1'
         PASSWORD = 'password123'
     }
    options {
        timeout(time: 1 , unit: 'MINUTES')

    }

    stages {



        stage('Setup') {
            steps {
                
                echo "Commit: ${env.GIT_COMMIT}"
                echo "my creds: ${SERVER_CREDS}"
                echo "my username: ${SERVER_CREDS_USR}"
                 echo "my password: ${SERVER_CREDS_PSW}"
               sh  "pip install -r requirements.txt"  
            }
        }
        stage('Test') {
            steps {
                echo "Commit: ${env.GIT_COMMIT}"
                sh '/var/lib/jenkins/.local/bin/pytest'     
             } 
            }
        }
    
}
