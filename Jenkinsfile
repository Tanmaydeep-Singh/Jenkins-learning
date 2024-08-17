pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                // The provided script doesn't include a build step, but if needed, you can add it here
                echo "No build step defined"
            }
        }
        stage('Run Application') {
            steps {
                // Start the application
                sh 'node app.js &'
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
