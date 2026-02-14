pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/KedarSalunkhe911/vote.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker-compose build vote result'
            }
        }
    }
}
