// Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Divya-Krishna99/docker-website'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-jenkins-website .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f jenkins-website || true'
                sh 'docker run -d --name jenkins-website -p 8081:80 my-jenkins-website'
            }
        }
    }
}
