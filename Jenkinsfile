pipeline {
    agent any

    options {
        timeout(time: 1 , unit: 'MINUTES')

    }

    stages {



        stage('Setup') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'server-creds', usernameVariable: 'myuser', passwordVariable: 'mypassword')]){
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
                echo "Commit: ${env.GIT_COMMIT}"
                sh '/var/lib/jenkins/.local/bin/pytest'     
             } 
            }
        }
    
}
