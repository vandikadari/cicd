pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/<your-username>/<your-repo>.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'pip install -r requirements.txt' // Ensure you have a requirements.txt
                }
            }
        }
        stage('Unit Testing') {
            steps {
                script {
                    sh 'pytest' // Assuming you have tests written with pytest
                }
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t <your-dockerhub-username>/<your-image-name> .'
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'docker login -u <your-dockerhub-username> -p <your-dockerhub-password>'
                    sh 'docker push <your-dockerhub-username>/<your-image-name>'
                }
            }
        }
        stage('Deploy to AWS') {
            steps {
                script {
                    // Deployment script goes here
                    // For example, using SSH to deploy on EC2
                }
            }
        }
    }
}
