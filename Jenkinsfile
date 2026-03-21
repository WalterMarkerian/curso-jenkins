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