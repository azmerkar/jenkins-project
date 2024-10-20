pipeline {
    agent any
    environment {
        // IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
        // IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
        // KUBECONFIG = credentials('kubeconfig-credentials-id')
          benim_adim = 'mehmet'

    }
    stages {

        stage('Setup') {
            steps {
                sh  "pip install -r requirements.txt"     
            }
        }
        stage('Test') {
            steps {
                sh "export PATH=$PATH:/var/lib/jenkins/.local/bin"
                sh "pytest"
                sh "whoami"
             } 
            }
        }
    
}
