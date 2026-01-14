pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo '📥 Cloning repository...'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkinswave:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop jenkinswave || true
                docker rm jenkinswave || true
                docker run -d -p 8085:80 --name jenkinswave jenkinswave
                '''
            }
        }
    }

    post {
        success {
            echo '✅ CI/CD Pipeline Completed Successfully!'
        }
    }
}
