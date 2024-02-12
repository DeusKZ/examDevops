pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Frontend') {
            steps {
                dir('client') {
                    script {
                        sh 'docker build -t frontend .'
                    }
                }
            }
        }

        stage('Build Backend') {
            steps {
                dir('server') {
                    script {
                        sh 'docker build -t backend .'
                    }
                }
            }
        }

        stage('Publish Locally') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        always {
            script {
                sh 'docker-compose down'
            }
        }
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
