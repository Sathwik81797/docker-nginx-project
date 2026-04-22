pipeline {
    agent any

    environment {
        IMAGE = "nginx-app"
        CONTAINER = "nginx-container"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Sathwik81797/docker-nginx-project.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop $CONTAINER || true'
                sh 'docker rm $CONTAINER || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name $CONTAINER $IMAGE'
            }
        }
    }
}
