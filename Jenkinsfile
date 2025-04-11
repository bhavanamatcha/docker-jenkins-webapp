pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/bhavanamatcha/docker-jenkins-webapp.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t static-site .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Docker container...'
                sh '''
                    docker stop static-site || true
                    docker rm static-site || true
                    docker run -d -p 8081:80 --name static-site static-site
                '''
            }
        }
    }
}

