pipeline {    agent any
    environment {
        DOCKER_IMAGE_NAME = "my-app-image"    }
    stages {
        stage('Clone Repository') {            steps {
                git 'https://github.com/PalmAngels521/new.git'            }
        }
        stage('Install Dependencies') {            steps {
                script {                    sh 'npm install'
                }            }
        }
        stage('Run Tests') {            steps {
                script {                    sh 'npm test' 
                }            }
        }
        stage('Build Docker Image') {            steps {
                script {                    sh 'docker build -t $DOCKER_IMAGE_NAME .'
                }            }
        }
        stage('Push Docker Image') {            steps {
                script {                    sh 'docker push $DOCKER_IMAGE_NAME'
                }            }
        }    }
    post {
        always {            sh 'docker system prune -f'
        }    }
}
