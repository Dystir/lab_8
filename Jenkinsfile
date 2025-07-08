pipeline {
    agent any

    stages {
        stage('Clone Source Code') {
            steps {
                git url: 'https://github.com/Dystir/lab_8.git', branch: 'main'
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
                    dockerImage.run("-d -p 5000:5000 --name flask-lab8")
                }
            }
        }
    }
}
