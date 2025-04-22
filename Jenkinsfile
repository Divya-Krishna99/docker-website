pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'mydockerimage'
        DOCKER_CONTAINER = 'mydockercontainer'
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
                    sh '''
                    docker rm -f $DOCKER_CONTAINER || true
                    docker run -d --name $DOCKER_CONTAINER -p 8080:80 $DOCKER_IMAGE
                    '''
                }
            }
        }
    }
}
