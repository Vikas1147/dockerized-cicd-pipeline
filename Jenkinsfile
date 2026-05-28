pipeline {
agent any

```
environment {
    COMPOSE_PROJECT_NAME = "devops-platform"
}

stages {

    stage('Clone Repository') {
        steps {
            git branch: 'main',
                url: 'https://github.com/Vikas1147/dockerized-cicd-pipeline.git'
        }
    }

    stage('Build Docker Images') {
        steps {
            bat 'docker compose build'
        }
    }

    stage('Cleanup Old Containers') {
        steps {
            bat 'docker rm -f backend_container || exit 0'
            bat 'docker rm -f frontend_container || exit 0'
            bat 'docker rm -f redis_container || exit 0'
            bat 'docker rm -f nginx_container || exit 0'
        }
    }

    stage('Stop Existing Containers') {
        steps {
            bat 'docker compose down || exit 0'
        }
    }

    stage('Start Containers') {
        steps {
            bat 'docker compose up -d'
        }
    }

    stage('Verify Running Containers') {
        steps {
            bat 'docker ps'
        }
    }

    stage('Verify Docker Network') {
        steps {
            bat 'docker network ls'
        }
    }

    stage('Verify Docker Volumes') {
        steps {
            bat 'docker volume ls'
        }
    }

    stage('Application Health Check') {
        steps {
            bat 'curl http://localhost'
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

    always {
        bat 'docker ps'
    }
}
```

}
