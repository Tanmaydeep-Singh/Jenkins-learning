pipeline {
    agent { docker {image 'node:13.8'} }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
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
                // The provided script doesn't include a build step, but if needed, you can add it here
                sh 'node --version'
                echo "No build step defined"
            }
        }
            stage('Test') {
            steps {
                // Run tests if any are defined
                echo "No tests defined"
            }
        }
    }

    post {
        always {
            // Actions to be executed after the stages, regardless of the build result
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
