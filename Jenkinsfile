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
            bat 'docker run -d -p 8086:80 jenkinswave'  
        }
    }
}
