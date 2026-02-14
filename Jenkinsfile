pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/KedarSalunkhe911/vote.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t kedarsalunkhe911/vote-app:latest ./vote'
            }
        }

        stage('Push to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS')]) {
                    
                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    docker push kedarsalunkhe911/vote-app:latest
                    '''
                }
            }
        }
    }
}

