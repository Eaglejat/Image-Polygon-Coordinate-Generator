pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/Eaglejat/Image-Polygon-Coordinate-Generator.git'
            }
        }

        stage('Prepare Dockerfile') {
            steps {
                sh '''
                cat <<EOF > Dockerfile
                FROM nginx:alpine
                COPY . /usr/share/nginx/html
                EXPOSE 80
                CMD ["nginx", "-g", "daemon off;"]
                EOF
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t html-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f html-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5431:80 --name html-container html-app'
            }
        }
    }
}
