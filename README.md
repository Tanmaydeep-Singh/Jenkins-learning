// Declarative pipeline
pipeline {
    agent any  // Specifies that the pipeline can run on any available Jenkins agent.

    stages {  // Defines the stages of the pipeline.
        stage('Build') {  // A stage named "Build".
            steps {  // The specific steps to be executed in this stage.
                echo "Build"  // Prints "Build" to the console output.
            }
        }
        stage('Test') {  // A stage named "Test".
            steps {  // The specific steps to be executed in this stage.
                echo "Test"  // Prints "Test" to the console output.
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
        changed {  // Runs only if the build result has changed compared to the previous build (e.g., from success to failure).
            echo "Failed"  // Prints "Failed" to the console output. (This could be a mistake; it might be intended to print something like "Status changed" instead.)
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

