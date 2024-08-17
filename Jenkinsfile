pipeline {
      agent {
        docker {
            image 'node:16'
        }
    }

    environment {
        // Update the Docker home and PATH variables if needed
        dockerHome = tool 'MyDocker'
        PATH = "${dockerHome}/bin:${env.PATH}"
    }

    stages {
        stage('Check Docker') {
            steps {
                script {
                    sh 'node --version'
                    // sh 'docker version'

                }
            }
        }

        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                echo 'No tests defined for now'
                // Replace with actual test command when tests are added
            }
        }

        // stage('Build Docker Image') {
        //     steps {
        //         script {
        //             // Build Docker image and tag it
        //             dockerImage = docker.build('tanmaydeep/jankinstest:latest')
        //             echo 'Docker image built'
        //         }
        //     }
        // }

        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             // Push Docker image to Docker Hub
        //             docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
        //                 dockerImage.push('latest')
        //             }
        //             echo 'Docker image pushed'
        //         }
        //     }
        //  }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Add deployment steps here
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
