pipeline {
    agent any

    environment {
        IMAGE_NAME = "first-api-rest"
        CONTAINER_NAME = "first-api-rest-container"
    }

    stages {
        stage('Checkout') {
            steps {
                // Jenkins descargará el código de GitHub automáticamente
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                echo 'Construyendo la imagen Docker...'
                // Usamos el Dockerfile que debe estar en tu repo
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando en el puerto 8081...'
                sh "docker stop ${CONTAINER_NAME} || true"
                sh "docker rm ${CONTAINER_NAME} || true"
                sh "docker run -d -p 8081:8080 --name ${CONTAINER_NAME} ${IMAGE_NAME}:latest"
            }
        }
    }
}