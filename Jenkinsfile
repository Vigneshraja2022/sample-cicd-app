pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Vigneshraja2022/sample-cicd-app'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-cicd-app:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop sample-app || true
                docker rm sample-app || true
                docker run -d -p 5000:5000 --name sample-app sample-cicd-app
                '''
            }
        }
    }
}
