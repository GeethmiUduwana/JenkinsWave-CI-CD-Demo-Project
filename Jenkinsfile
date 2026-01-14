pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/GeethmiUduwana/JenkinsWave-CI-CD-Demo-Project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t jenkinswave .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker container...'
                // Stop old container if exists
                bat '''
                for /f "tokens=*" %%i in ('docker ps -q --filter "name=jenkinswave"') do docker stop %%i
                for /f "tokens=*" %%i in ('docker ps -aq --filter "name=jenkinswave"') do docker rm %%i
                docker run -d -p 8085:80 --name jenkinswave jenkinswave
                '''
            }
        }
    }
}
