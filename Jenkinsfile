
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t mlops-uat-demo .'
            }
        }

        stage('Run Application') {
            steps {
                bat 'docker run --rm mlops-uat-demo'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'docker run --rm -v "%WORKSPACE%:/app" -w /app python:3.12-slim sh -c "pip install -r requirements.txt && python -m pytest -v"'
            }
        }
    }
}
