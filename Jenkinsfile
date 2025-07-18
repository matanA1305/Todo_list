pipeline {
    agent any

    environment {
        IMAGE_NAME = 'yp3yp3/to_do_list'
    }
    stages {
        stage('Build Docker Image') {
        
}
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh '''
                    docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
                    docker tag myapp $DOCKER_USERNAME/myapp:latest
                    docker push $DOCKER_USERNAME/myapp:latest
                    echo $DOCKER_PASSWORD | docker login --username foo --password-stdin
                    docker tag myapp $DOCKER_USERNAME/$IMAGE_NAME:latest
                    docker push $DOCKER_USERNAME/$IMAGE_NAME:latest
                    '''
                    }
                }
            }
        }
    }


