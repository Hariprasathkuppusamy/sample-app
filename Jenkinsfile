pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-app:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f sample-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name sample-app -p 5000:5000 sample-app:latest'
            }
        }
    }
}
