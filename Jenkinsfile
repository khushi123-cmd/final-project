pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Check Files') {
            steps {
                bat 'echo Checking project files'
                bat 'dir'
                bat 'if not exist Dockerfile exit 1'
                bat 'if not exist docker-compose.yml exit 1'
                bat 'if not exist index.html exit 1'
            }
        }

        stage('Build & Deploy using Docker Compose') {
            steps {
                bat '''
                docker compose down
                docker compose up -d --build
                '''
            }
        }

        stage('Success') {
            steps {
                bat 'echo HTML + CSS site deployed successfully '
            }
        }
    }
}
