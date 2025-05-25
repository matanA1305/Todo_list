pipline {
    agent any

    stages {
        stage('Build docker image') {
            when { not {branch 'master' } }
            steps {
                sh '''
                    docker build -t myapp ./app
                    docker tag myapp yp3yp3/to_do_list 
                    docker tag mt app yp3yp3/to_do_list:latest
                    '''
            }
        }
         stage('run app with docker compose') {
            steps {
                sh '''
                    docker-compose down || true
                    docker-compose up -d
                    docker-compose ps
                    '''
            }
         }
         stage('run tests') {
            when {
                sh '''
                python3 -m venv .venv
                . . venv/bin/activate
                pip install -r test/requirements.txt
                pytest ./test
                '''
            }
            }
         }
