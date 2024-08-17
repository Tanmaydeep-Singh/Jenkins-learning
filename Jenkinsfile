pipeline {
    agent any

    environment {
        dockerHome = tool name: 'MyDocker', type: 'DockerTool'
        PATH = "$dockerHome/bin:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                sh 'node -v'
                sh 'npm -v'
                echo "Checkout"
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
                echo "Test"
            }
        }
    }

    post {
        always {
            echo "Awesome"
        }
        success {
            echo "Running on success"
        }
        failure {
            echo "Failed"
        }
        changed {
            echo "Status Changed"
        }
    }
}

// Old Scripted Approach
// node {
//     stage('Build') {
//         echo "Build"
//     }
//     stage('Test') {
//         echo "Test"
//     }
// }
