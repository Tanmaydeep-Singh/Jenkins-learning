// Declarative pipeline

pipeline {
    agent any  // Specifies that the pipeline can run on any available Jenkins agent.

    // Optionally, you can define a specific Docker image to use for this pipeline
    // Uncomment the following line if you want to use a Maven Docker container
    // agent { docker { image 'maven:3.6.3'} }

    // Defines environment variables used in the pipeline
    environment {
        dockerHome = tool 'MyDocker'  // Jenkins tool named "MyDocker" is configured and its path is set to dockerHome.
        PATH = "$dockerHome/bin$PATH"  // Updates the PATH environment variable to include Docker and Maven.
    }

    stages {  // Defines the stages of the pipeline.
            stage('Checkout') {  // A stage named "Checkout".
            steps {  // The specific steps to be executed in this stage.
                sh 'node -v'  // Prints the Node.js version to the console output.
                sh 'npm -v'   // Prints the npm version to the console output.
                echo "Checkout"
            }
        }
        stage('Install Dependencies') {  // A stage named "Install Dependencies".
            steps {  // The specific steps to be executed in this stage.
                sh 'npm install'  // Installs Node.js dependencies from package.json.
            }
        }
        stage('Build') {  // A stage named "Build".
            steps {  // The specific steps to be executed in this stage.
                sh 'npm run build'  // Runs the build script defined in package.json (if applicable).
            }
        }
        stage('Test') {  // A stage named "Test".
            steps {  // The specific steps to be executed in this stage.
                sh 'npm test'  // Runs the test script defined in package.json.
                echo "Test"
            }
        }
    }

    post {  // Post actions that are executed after the stages have completed.
        always {  // Runs regardless of the build result (success, failure, or aborted).
            echo "Awesome"  // Prints "Awesome" to the console output.
        }
        success {  // Runs only if the build is successful.
            echo "Running on success"  // Prints "Running on success" to the console output.
        }
        failure {  // Runs only if the build fails.
            echo "Failed"  // Prints "Failed" to the console output.
        }
        changed {  // Runs only if the build result has changed compared to the previous build (e.g., from success to failure or vice versa).
            echo "Status Changed"  // Prints "Status Changed" to the console output.
        }
    }
}

// Old Scripted Approach
// node {
//     stage('Build') {
//         echo "Build"  // Prints "Build" to the console output.
//     }
//     stage('Test') {
//         echo "Test"  // Prints "Test" to the console output.
//     }
// }
