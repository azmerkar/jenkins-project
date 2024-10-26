pipeline {
    agent any

     environment {
         DB_HOST = '192.143.06.06'
         USERNAME = 'user1'
         PASSWORD = 'password123'
     }
    options {
        timeout(time: 1 , unit: 'MINUTES')

    }

    stages {

        stage('lint and formatting'){
               steps{
                   sh 'sleep  10'
               }
        }

        stage('Setup') {
            steps {
                echo "Commit: ${env.GIT_COMMIT}"
                echo "The enviroment variables are ${DB_HOST} ,${USERNAME}, ${PASSWORD}"
                sh  "pip install -r requirements.txt"  
            }
        }
        stage('Test') {
            steps {
                echo "Commit: ${env.GIT_COMMIT}"
                sh '/var/lib/jenkins/.local/bin/pytest     
             } 
            }
        }
    
}
