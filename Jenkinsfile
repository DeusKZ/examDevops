pipeline {
    agent any

    stages {
        stage('Checkout Repository') {
            steps {
                script {
                    git 'https://github.com/DeusKZ/examDevops.git'
                }
            }
        }

        stage('Build and Run Docker Container') {
            steps {
                script {
                       docker build -t examDevops:latest .
                       docker run -d --examDevops -p 8080:8080 devops:latest
                }
            }
        }

        stage('Check if Docker Container is Running') {
            steps {
                script {
                       docker ps | grep examDevops
                }
            }
        }

        stage('Stop Docker Container') {
            steps {
                script {
                       docker stop examDevops
                }
            }
        }
    }
}
