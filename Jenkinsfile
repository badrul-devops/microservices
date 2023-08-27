pipeline {
    agent none
    
    stages {
        stage('Run Microservices') {
            matrix {
                axes {
                    axis {
                        name 'MICROSERVICE'
                           values 'cart-microservice-nodejs', 'eureka-discovery-server'//,'offers-microservice-spring-boot', 'shoes-microservice-spring-boot', 'ui-web-app-reactjs', 'wishlist-microservice-python', 'zuul-api-gateway'
                    }
                }
                stages {
                    stage('Build and Deploy') {
                        agent {
                            label "${MICROSERVICE}-node" // Use the appropriate label for each microservice
                        }
                        steps {
                            script {
                                echo "Building and deploying ${MICROSERVICE}"

                                // Pull code for the microservice from its specific folder
                                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [url: "https://github.com/badrul-devops/microservices.git"], extensions: [[$class: 'PathRestriction', excludedRegions: '', includedRegions: "${MICROSERVICE}/.*"]]])

                                // Navigate to the microservice folder
                                dir("${MICROSERVICE}") {
                                    // Build Docker image
                                    sh "docker build -t badrul11/${MICROSERVICE} ."

                                    // Deploy the Docker container (modify as needed)
                                    // sh "docker run -d --name ${MICROSERVICE}-container ${MICROSERVICE}"
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
