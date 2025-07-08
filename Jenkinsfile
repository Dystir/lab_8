pipeline {
    agent any

    stages {
        stage('Clone Source Code') {
            steps {
                git 'https://github.com/Dystir/lab_8.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-lab8")
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    sh 'docker rm -f flask-lab8 || true'
                    dockerImage.run('-d -p 5000:5000 --name flask-lab8')
                }
            }
        }
    }
}
