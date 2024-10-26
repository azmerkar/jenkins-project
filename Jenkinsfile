pipeline {
    agent any
    parameters{
        string(name: 'ENVIRONMENT', defaulValue: 'dev', description: 'Specify test environment')
        booleanParam(name: 'RUN_TESTS', defaulValue: true, description: 'Run tests in pipelin'  )
    }

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
            when{
                expression{
                    params.RUN_TESTS == true 
                }
            }
            steps {
                echo "Commit: ${env.GIT_COMMIT}"
                echo "testing application"     
             } 
            }

        stage('Deploy') {

            steps {
                echo "deploying application to ${params.ENVIRONMENT}"     
             } 
            }            
        }
    
}
