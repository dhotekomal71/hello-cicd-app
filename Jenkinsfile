pipeline {
    agent { label 'slave2' }

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t hello-app .'
            }
        }

        stage('Run') {
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
