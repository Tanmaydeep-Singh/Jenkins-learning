pipeline {
    agent any

    environment {
         node = tool 'node'
         PATH = "${nodejs}/bin:${env.PATH}"

    }
   

    stages {
        stage('Check Version') {
            steps {
                script {
                    // Check Node.js version
                    sh 'node --version'
                    
                    // Check Docker version (ensure Docker is installed on Jenkins agent)
                    sh 'docker --version'
                }
            }
        }
    }
}



// WORKING VERSION
// pipeline {
//       agent {
//         docker {
//             image 'node:16'
//         }
//     }

//     environment {
//         dockerHome = tool 'MyDocker'
//         PATH = "${dockerHome}/bin:${env.PATH}"
//     }

//     stages {
//         stage('Check Docker') {
//             steps {
//                 script {
//                     sh 'node --version'
//                 }
//             }
//         }

//         stage('Checkout') {
//             steps {
//                 echo 'Checking out code...'
//                 checkout scm
//             }
//         }

//         stage('Install Dependencies') {
//             steps {
//                 script {
//                     sh 'npm install'
//                 }
//             }
//         }

//         stage('Run Tests') {
//             steps {
//                 echo 'No tests defined for now'
//                 // Replace with actual test command when tests are added
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo 'Deploying application...'
//             }
//         }
//     }

//     post {
//         always {
//             echo 'Pipeline finished.'
//         }
//         success {
//             echo 'Build and deployment successful'
//         }
//         failure {
//             echo 'Build or deployment failed'
//         }
//     }
// }
