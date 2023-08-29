// // pipeline {
// //     agent any

// //     stages {
// //         stage('Clone Repository') {
// //             steps {
// //                 // Clone the main repository
// //                 checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/badrul-devops/microservices.git']])
// //             }
// //         }

// //         stage('Build Microservices') {
// //             steps {
// //                 script {
// //                     // List of microservices
// //                     def microservices = [
// //                         'cart-microservice-nodejs',
// //                         'offers-microservice-spring-boot',
// //                         'shoes-microservice-spring-boot',
// //                         'ui-web-app-reactjs',
// //                         'wishlist-microservice-python',
// //                         'zuul-api-gateway'
// //                     ]

// //                     // Loop through each microservice and build its Docker image
// //                     for (def service in microservices) {
// //                         dir(service) {
// //                             // Build the Docker image for the microservice
// //                             sh "docker build -t badrul11/$service ."
// //                             // sh "docker push badrul11/$service"
// //                         }
// //                     }
// //                 }
// //             }
// //         }
// //     }
// // }

//  pipeline {
//     agent any

//     stages {
//         stage('Clone Repository') {
//             steps {
//                 // Clone the main repository
//                 checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/badrul-devops/microservices.git']])
//             }
//         }

//         stage('Build Microservices') {
//             matrix {
//                 axes {
//                     axis {
//                         name 'MICROSERVICE'
//                         values 'cart-microservice-nodejs', 'offers-microservice-spring-boot', 'shoes-microservice-spring-boot', 'ui-web-app-reactjs', 'wishlist-microservice-python', 'zuul-api-gateway'
//                     }
//                 }
//                 stages {
//                     stage("Build and Push ${MICROSERVICE}") {
//                         steps {
//                             dir("${MICROSERVICE}") {
//                                 // Build the Docker image for the microservice
//                                 sh "docker build -t badrul11/${MICROSERVICE} ."
//                                 sh "docker push badrul11/${MICROSERVICE}"
//                             }
//                         }
//                     }
//                 }
//             }
//         }
//     }

//     // post {
//     //     always {
//     //         // Clean up Docker images after the pipeline finishes
//     //         sh 'docker system prune -af'
//     //     }
//     // }
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

        stage('Build Cart Microservice') {
            steps {
                dir('cart-microservice-nodejs') {
                    // Build the Docker image for the Cart Microservice
                    sh 'docker build -t badrul11/cart-microservice-nodejs .'
                    //sh 'docker push badrul11/cart-microservice-nodejs'
                }
            }
        }

        stage('Build Offers Microservice') {
            steps {
                dir('offers-microservice-spring-boot') {
                    // Build the Docker image for the Offers Microservice
                    sh 'docker build -t badrul11/offers-microservice-spring-boot .'
                    //sh 'docker push badrul11/offers-microservice-spring-boot'
                }
            }
        }

        // Repeat similar stages for the other microservices

        stage('Build Zuul API Gateway') {
            steps {
                dir('zuul-api-gateway') {
                    // Build the Docker image for the Zuul API Gateway
                    sh 'docker build -t badrul11/zuul-api-gateway .'
                    //sh 'docker push badrul11/zuul-api-gateway'
                }
            }
        }
        stage('Build shoes microservice spring boot') {
            steps {
                dir('shoes-microservice-spring-boot') {
                    // Build the Docker image for the Zuul API Gateway
                    sh 'docker build -t badrul11/shoes-microservice-spring-boot .'
                    //sh 'docker push badrul11/shoes-microservice-spring-boot'
                }
            }
        }
        stage('Build ui web app reactjs') {
            steps {
                dir('ui-web-app-reactjs') {
                    // Build the Docker image for the Zuul API Gateway
                    sh 'docker build -t badrul11/ui-web-app-reactjs .'
                    //sh 'docker push badrul11/ui-web-app-reactjs'
                }
            }
        }
        stage('Build wishlist microservice python') {
            steps {
                dir('wishlist-microservice-python') {
                    // Build the Docker image for the Zuul API Gateway
                    sh 'docker build -t badrul11/wishlist-microservice-python .'
                    //sh 'docker push badrul11/wishlist-microservice-python'
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
