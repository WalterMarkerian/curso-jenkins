pipeline {
    agent any

    stages {
        stage('Build con Maven en Docker') {
            steps {
                script {
                    def workspace = env.WORKSPACE
                    sh """
                    docker run --rm \
                      -v ${workspace}/first-api-rest:/app \
                      -w /app \
                      maven:3.9.9-eclipse-temurin-21 \
                      mvn clean install
                    """
                }
            }
        }
    }
}