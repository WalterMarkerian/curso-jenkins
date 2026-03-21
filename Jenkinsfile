pipeline {
    agent any

    stages {
        stage('Build con Maven en Docker') {
            steps {
                dir('first-api-rest') {
                    sh '''
                    docker run --rm \
                      -v $(pwd):/app \
                      -w /app \
                      maven:3.9.9-eclipse-temurin-21 \
                      mvn clean install
                    '''
                }
            }
        }
    }
}