pipeline {
    agent any

    stages {

        stage('lint and formatting'){
            stages{
                  stage('linting'){
                     steps{
                         echo 'linting'
                     }

                  }

                  stage('formatting'){
                    steps{
                       echo 'formatting'

                    }
                  }
            }
        }

        stage('Setup') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'server-creds',
                usernameVariable: "myuser" ,passwordVariable: "mypassword"  )]) {
                    
                    sh '''
                    echo ${myuser}
                    echo ${mypassword}
                    '''
                }
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
