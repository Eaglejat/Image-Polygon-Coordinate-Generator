pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')   // auto trigger (later webhook se replace kar sakte ho)
    }

    environment {
        IMAGE_NAME = "html-app"
        CONTAINER_NAME = "html-container"
        PORT = "3000"
    }

    stages {

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

        stage('Verify Deployment') {
            steps {
                sh 'docker ps | grep $CONTAINER_NAME'
            }
        }

        stage('Cleanup Old Images') {
            steps {
                sh 'docker image prune -f'
            }
        }
    }
}
