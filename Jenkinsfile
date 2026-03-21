pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build con Maven en Docker') {
            steps {
                sh '''
                docker run --rm \
                -v /var/lib/docker/volumes/jenkins_home/_data/workspace/jenkins-test-pipeline/first-api-rest:/app \
                -w /app \
                maven:3.9.9-eclipse-temurin-21 \
                mvn clean install
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t first-api-rest:latest first-api-rest
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop first-api-rest || true
                docker rm first-api-rest || true

                docker run -d -p 8081:8080 --name first-api-rest first-api-rest:latest
                '''
            }
        }
    }
}