pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
                sh 'test -f app/app.py'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t cicd-demo:${BUILD_NUMBER} .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Docker container...'

                sh '''
                    docker stop cicd-demo-container || true
                    docker rm cicd-demo-container || true

                    docker run -d \
                        --name cicd-demo-container \
                        -p 5000:5000 \
                        cicd-demo:${BUILD_NUMBER}
                '''

                echo 'Deployment successful!'
            }
        }
    }
}
