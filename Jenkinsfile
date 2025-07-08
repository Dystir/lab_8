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
                    // Build Docker image và lưu lại object để dùng sau
                    dockerImage = docker.build("flask-lab8")
                }
            }
        }

        stage('Deploy Container') {
            steps {
                script {
                    // Xoá container cũ nếu tồn tại để tránh lỗi conflict
                    sh 'docker rm -f flask-lab8 || true'

                    // Chạy container mới
                    dockerImage.run('-d -p 5000:5000 --name flask-lab8')
                }
            }
        }
    }
}
