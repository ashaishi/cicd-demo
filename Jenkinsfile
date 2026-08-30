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
    }
}
