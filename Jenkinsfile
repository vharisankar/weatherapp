pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/vharisankar/weatherapp.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t weather-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop weather-container || true'
                sh 'docker rm weather-container || true'
                sh 'docker run -d -p 8000:8000 --name weather-container weather-app'
            }
        }
    }
}
