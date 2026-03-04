pipeline {
    agent { label 'java_slave' }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/dhotekomal71/hello-cicd-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hello-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop hello-container || true
                docker rm hello-container || true
                docker run -d -p 8080:80 --name hello-container hello-app
                '''
            }
        }
    }
}
