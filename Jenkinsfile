pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Debug') {
            steps {
                sh 'echo ===== PWD ====='
                sh 'pwd'

                sh 'echo ===== ROOT ====='
                sh 'ls -la'

                sh 'echo ===== FIRST-API-REST ====='
                sh 'ls -la first-api-rest || echo "NO EXISTE LA CARPETA"'
            }
        }

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