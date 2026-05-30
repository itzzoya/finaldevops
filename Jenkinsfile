pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/itzzoya/finaldevops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t finaldevops .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop finaldevops-container || true'
                sh 'docker rm finaldevops-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 80:80 --name finaldevops-container finaldevops'
            }
        }
    }
}