// Jenkinsfile
// Declarative pipeline for CI/CD

pipeline {
    agent any

    environment {
        APP_NAME = 'dockerized-nodejs-CiCd'
        IMAGE_NAME = 'dockerized-nodejs-CiCd:latest'
        DEPLOY_PORT = 3000
        RECIPIENT_EMAIL = 'ahmadkodify@gmail.com' // Replace with your email
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Cloning repository from GitHub...'
                git branch: 'main', url: 'https://github.com/Ahmad-kodify/dockerized-nodejs-cicd'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Node.js dependencies...'
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Deploy Docker Container') {
            steps {
                echo 'Deploying Docker container...'
                // Stop previous container if running
                sh "docker rm -f ${APP_NAME} || true"
                // Run container
                sh "docker run -d --name ${APP_NAME} -p ${DEPLOY_PORT}:${DEPLOY_PORT} ${IMAGE_NAME}"
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline succeeded!'
            mail to: "${RECIPIENT_EMAIL}",
                 subject: "SUCCESS: ${APP_NAME} Deployment",
                 body: "The Dockerized Node.js app has been deployed successfully!"
        }
        failure {
            echo '❌ Pipeline failed!'
            mail to: "${RECIPIENT_EMAIL}",
                 subject: "FAILED: ${APP_NAME} Deployment",
                 body: "The deployment of Dockerized Node.js app failed. Check Jenkins logs."
        }
    }
}
