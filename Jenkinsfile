pipeline {
    agent any
    parameters{
        string(name: 'ENVIRONMENT', defaultValue: 'dev', description: 'Specify test environment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run tests in pipeline'  )
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
                catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
             sh '''
                    source ~/.bashrc
                    pytest --version
                    pytest
               '''
             } 
            }
        }
        stage('Deploy') {
            input {
                message "Do you want to proceed further?"
                ok "Yes"
            }
            steps {
                echo "Deploying application to ${params.ENVIRONMENT}"     
             } 
            }            
        }
    
}
