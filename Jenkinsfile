pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/bhavanamatcha/docker-jenkins-webapp.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build step (if any)'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker build -t static-site .
                    docker stop static-site || true
                    docker rm static-site || true
                    docker run -d -p 80:80 --name static-site static-site
                '''
            }
        }
    }
}
