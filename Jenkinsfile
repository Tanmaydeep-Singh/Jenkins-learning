// Declarative pipeline

pipeline{
    agent any
    // agent { docker { image 'maven:3.6.3'} }
    environment {
        dockerHome = tool 'MyDocker'
        mavenHome = tool 'MyMaven'
        PATH = "$dockerHome/bin: $mavenHome/bin:$PATH"
    }

    stages{
        stage('Checkout')
        {
            steps{
                sh 'mvn --version'
                sh 'docker version'
                echo "Checkout"
            }
        }
        stage('Compile')
        {
            steps{
                sh "mvn clean compile"
            }
        }
        stage('Test')
        {
            steps{
                sh "mvn test"
                echo "Test"
            }
        }
    }
    post{
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
            echo "Failed"
        
        }
    }
}































// Old Scripted Approach
// node{
//     stage('Build'){
//         echo "Buid"
//     }
//     stage('Test'){
//         echo "Test"
//     }
// }