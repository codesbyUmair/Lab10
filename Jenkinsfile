pipeline {
    agent any

    environment {
        // Define environment variables if needed
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/NaseemKhan005/react-bank-app'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install frontend dependencies
                    dir('frontend') {
                        sh 'npm install'
                    }
                    // Install backend dependencies
                    dir('backend') {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    dir('frontend') {
                        sh 'npm run build'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    dir('frontend') {
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Dockerize and Deploy') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t react-app .'
                    // Run containers using Docker Compose
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}

