pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'mydockerimage'
        DOCKER_CONTAINER = 'mydockercontainer'
        HOST_PORT = '8081'  // Configurable port to avoid conflict
        CONTAINER_PORT = '80'  // Port inside the container
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Uses the repository already configured in Jenkins
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Remove the container if it exists
                    sh 'docker rm -f $DOCKER_CONTAINER || true'
                    
                    // Run the container on a configurable port
                    sh "docker run -d --name $DOCKER_CONTAINER -p $HOST_PORT:$CONTAINER_PORT $DOCKER_IMAGE"
                }
            }
        }
    }
}
