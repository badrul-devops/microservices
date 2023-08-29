// pipeline {
//     agent any

//     stages {
//         stage('Clone Repository') {
//             steps {
//                 // Clone the main repository
//                 checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/badrul-devops/microservices.git']])
//             }
//         }

//         stage('Build Microservices') {
//             steps {
//                 script {
//                     // List of microservices
//                     def microservices = [
//                         'cart-microservice-nodejs',
//                         'offers-microservice-spring-boot',
//                         'shoes-microservice-spring-boot',
//                         'ui-web-app-reactjs',
//                         'wishlist-microservice-python',
//                         'zuul-api-gateway'
//                     ]

//                     // Loop through each microservice and build its Docker image
//                     for (def service in microservices) {
//                         dir(service) {
//                             // Build the Docker image for the microservice
//                             sh "docker build -t badrul11/$service ."
//                             // sh "docker push badrul11/$service"
//                         }
//                     }
//                 }
//             }
//         }
//     }
// }

 pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the main repository
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/badrul-devops/microservices.git']])
            }
        }

        stage('Build Microservices') {
            matrix {
                axes {
                    axis {
                        name 'MICROSERVICE'
                        values 'cart-microservice-nodejs', 'offers-microservice-spring-boot', 'shoes-microservice-spring-boot', 'ui-web-app-reactjs', 'wishlist-microservice-python', 'zuul-api-gateway'
                    }
                }
                stages {
                    stage("Build and Push ${MICROSERVICE}") {
                        steps {
                            dir("${MICROSERVICE}") {
                                // Build the Docker image for the microservice
                                sh "docker build -t your-registry/${MICROSERVICE} ."
                                sh "docker push your-registry/${MICROSERVICE}"
                            }
                        }
                    }
                }
            }
        }
    }

    // post {
    //     always {
    //         // Clean up Docker images after the pipeline finishes
    //         sh 'docker system prune -af'
    //     }
    // }
}
