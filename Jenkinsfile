pipeline {
    agent any

    stages {

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
