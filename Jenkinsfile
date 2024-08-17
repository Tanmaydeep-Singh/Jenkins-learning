pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Tanmaydeep-Singh/Jenkins-learning'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('node-app')
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'tanmaydeep') {
                        docker.image('node-app').push('latest')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                // Deploy steps here, e.g., Kubernetes, Docker Swarm, etc.
                echo 'Deploying application...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
