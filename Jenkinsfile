pipeline {
    agent any
    environment {
        // IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
        // IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
        // KUBECONFIG = credentials('kubeconfig-credentials-id')
          benim_adim = 'mehmet'

    }
    stages {

        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/kodekloudhub/jenkins-project.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }
        stage('Setup') {
            steps {
                sh '''
                    # Sanal ortam oluşturma
                    python3 -m venv venv

                    # Sanal ortamı etkinleştir
                    . venv/bin/activate

                    # Gereksinimleri yükle
                    pip install -r requirements.txt

                    # pytest kurulumunu doğrulayın
                    pip install pytest
                '''            
            }
        }
        stage('Test') {
            steps {

                sh ". venv/bin/activate"
                sh "pytest"
                sh "whoami"
            }
        }
        // stage('Login to docker hub') {
        //     steps {
        //         withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
        //         sh 'echo ${dockerhubpwd} | docker login -u sanjeevkt720 --password-stdin'}
        //         echo 'Login successfully'
        //     }
        // }
        // stage('Build Docker Image')
        // {
        //     steps
        //     {
        //         sh 'docker build -t ${IMAGE_TAG} .'
        //         echo "Docker image build successfully"
        //         sh "docker images"
        //     }
        // }
        // stage('Push Docker Image')
        // {
        //     steps
        //     {
        //         sh 'docker push ${IMAGE_TAG}'
        //         echo "Docker image push successfully"
        //     }
        // }
        // stage('Deploy to EKS Cluster') {
        //     steps {
        //         sh "kubectl apply -f deployment.yaml"
        //         echo "Deployed to EKS Cluster"
        //     }
        // }
    }
}