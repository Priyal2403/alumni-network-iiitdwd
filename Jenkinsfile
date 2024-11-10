pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'ci/cd_test', url: 'https://github.com/Priyal2403/alumni-network-iiitdwd.git'
            }
        }
        stage('Build Backend Image') {
            steps {
                sh 'docker build -t aurum2403/server . -f server/Dockerfile'
                sh 'docker push aurum2403/server'
            }
        }
        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t aurum2403/client . -f client/Dockerfile'
                sh 'docker push aurum2403/client'
            }
        }
    }
}