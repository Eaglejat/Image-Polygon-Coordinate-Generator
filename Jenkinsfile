pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')   // auto trigger on code changes
    }

    environment {
        IMAGE_NAME = "html-app"
        CONTAINER_NAME = "html-container"
        PORT = "3000"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Eaglejat/Image-Polygon-Coordinate-Generator'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                -p $PORT:80 \
                --name $CONTAINER_NAME \
                $IMAGE_NAME:latest
                '''
            }
        }

        stage('Cleanup Old Images') {
            steps {
                sh 'docker image prune -f'
            }
        }
    }
}
