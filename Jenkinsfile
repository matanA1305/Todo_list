stage('Push Docker Image') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
            sh '''
            docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
            docker tag ${IMAGE_NAME} $DOCKER_USERNAME/$IMAGE_NAME:latest 
            docker push $DOCKER_USERNAME/$IMAGE_NAME:latest 
            '''
        }
    }
}
