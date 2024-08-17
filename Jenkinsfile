// Declarative pipeline

pipeline {
    agent any  // Specifies that the pipeline can run on any available Jenkins agent.

    // Optionally, you can define a specific Docker image to use for this pipeline
    // Uncomment the following line if you want to use a Maven Docker container
    // agent { docker { image 'maven:3.6.3'} }

    // Defines environment variables used in the pipeline
    environment {
        dockerHome = tool 'MyDocker'  // Jenkins tool named "MyDocker" is configured and its path is set to dockerHome.
        mavenHome = tool 'MyMaven'    // Jenkins tool named "MyMaven" is configured and its path is set to mavenHome.
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"  // Updates the PATH environment variable to include Docker and Maven.
    }

    stages {  // Defines the stages of the pipeline.
        stage('Checkout') {  // A stage named "Checkout".
            steps {  // The specific steps to be executed in this stage.
                sh 'mvn --version'  // Prints the Maven version to the console output.
                sh 'docker version'  // Prints the Docker version to the console output.
                echo "Checkout"  // Prints "Checkout" to the console output.
            }
        }
        stage('Compile') {  // A stage named "Compile".
            steps {  // The specific steps to be executed in this stage.
                sh "mvn clean compile"  // Runs Maven's clean and compile commands.
            }
        }
        stage('Test') {  // A stage named "Test".
            steps {  // The specific steps to be executed in this stage.
                sh "mvn test"  // Runs Maven's test command.
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
