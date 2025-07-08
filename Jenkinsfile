pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/<your-username>/flask-ci-cd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-app")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f flask-container || true'
                    dockerImage.run('-d -p 5000:5000 --name flask-container')
                }
            }
        }
    }
}
