pipeline {
    agent { docker { image 'node:16' } } 

    environment {
        dockerHome = tool 'MyDocker'
        PATH = "${dockerHome}/bin:${env.PATH}"
    }

    stages {
        stage('Check Docker') {
            steps {
                sh 'docker version'
            }
        }
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                echo 'No tests defined for now'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('tanmaydeep/jankinstest:latest')
                }
                echo 'Docker image built'
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build and deployment successful'
        }
        failure {
            echo 'Build or deployment failed'
        }
    }
}
