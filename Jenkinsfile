pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo ' Cloning repository...'
                git url: 'https://github.com/GeethmiUduwana/JenkinsWave-CI-CD-Demo-Project.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo ' Building Docker image...'
                bat 'docker build -t jenkinswave .'
            }
        }

        stage('Run Container') {
            steps {
                echo ' Running Docker container...'
                bat 'docker run -d -p 8085:80 jenkinswave'
            }
        }
    }
}
