// Declarative pipeline

pipeline{
    agent any
    stages{
        stage('Build')
        {
            steps{
                echo "Build"
            }
        }
        stage('Test')
        {
            steps{
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