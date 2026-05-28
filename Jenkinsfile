pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = "devops-platform"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'http://github.com/Vikas1147/dockerized-cicd-pipeline.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Stop Existing Containers') {
            steps {
                sh 'docker compose down || true'
            }
        }

        stage('Start Containers') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verify Running Containers') {
            steps {
                sh 'docker ps'
            }
        }

        stage('Verify Docker Network') {
            steps {
                sh 'docker network ls'
            }
        }

        stage('Verify Docker Volumes') {
            steps {
                sh 'docker volume ls'
            }
        }

        stage('Application Health Check') {
            steps {
                sh 'curl -f http://localhost || exit 1'
            }
        }
    }

    post {

        success {
            echo 'Deployment Successful!'
        }

        failure {
            echo 'Pipeline Failed!'
        }
    }
}