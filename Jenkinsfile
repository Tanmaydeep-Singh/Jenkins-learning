pipeline {
     agent { docker { image 'node:13.8' } }

    environment {
        dockerHome = tool name: 'MyDocker'
        PATH = "${dockerHome}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
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
                    dockerImage = docker.build('tanmaydeep/jankinstest:latest')
                }
            }
        }
        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             docker.withRegistry('https://registry.hub.docker.com', '07b7537e-2932-436c-8573-81aa3cab957e') {
        //                 docker.image(dockerImage).push('latest')
        //             }
        //         }
        //     }
        // }
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

// pipeline {
//     agent { docker { image 'node:13.8' } }

//     environment {
//         dockerHome = tool name: 'MyDocker'
//         PATH = "${dockerHome}/bin:${env.PATH}"
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 echo 'Checking out code...'
//                 // Add a checkout step if needed, e.g., git checkout
//             }
//         }
//         stage('Install Dependencies') {
//             steps {
//                 sh 'npm install'
//             }
//         }
//         stage('Build') {
//             steps {
//                 sh 'node --version'
//                 echo 'No build step defined'
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo 'No tests defined'
//             }
//         }
//         stage('Build Docker Image') {
//             steps {
//                 script {
//                     dockerImage = docker.build("tanmaydeep/test:latest")
//                 }
//             }
//         }
//         stage('Push Docker Image') {
//             steps {
//                 script {
//                     docker.withRegistry('', '07b7537e-2932-436c-8573-81aa3cab957e') {
//                         dockerImage.push('latest')
//                     }
//                 }
//             }
//         }
//     }

//     post {
//         always {
//             echo 'Pipeline completed'
//         }
//         success {
//             echo 'Build and run successful'
//         }
//         failure {
//             echo 'Build or run failed'
//         }
//     }
// }
