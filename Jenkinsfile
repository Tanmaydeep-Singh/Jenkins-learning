pipeline {
    agent { docker {image 'node:13.8'} }

    environment {
        dockerHome = tool name: 'MyDocker', type: 'DockerTool'
        PATH = "$dockerHome/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'checkout'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'node --version'
                echo "No build step defined"
            }
        }
        stage('Test') {
            steps {
                echo "No tests defined"
            }
        }
        stage('Build Docker Image')
        {
            steps {
                script {
                    dockerImage = docker.build("tanmaydeep/test:latest")
                }
            }
        }
        stage('Push Docker Image')
        {
            steps{
                script{
                    docker.withRegistry('', '07b7537e-2932-436c-8573-81aa3cab957e'){
                    dockerImage.push();
                    }
                }

            }
        }
    }

    post {
        always {
            echo "Pipeline completed"
        }
        success {
            echo "Build and run successful"
        }
        failure {
            echo "Build or run failed"
        }
    }
}
