pipeline {
    agent any
    environment {
        DOCKER_REGISTRY = 'Tspringer1204' 
        DOCKER_IMAGE = 'my-jenkins-image'
    }
    stages {
        stage('Test Docker Setup') {
            steps {
                script {
                    echo 'Testing Docker setup...'
                    sh 'docker --version'
                    sh 'docker images'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    sh 'docker build -t $DOCKER_REGISTRY/$DOCKER_IMAGE:latest .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    echo 'Pushing Docker image to Docker Hub...'
                    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_REGISTRY --password-stdin'
                    sh 'docker push $DOCKER_REGISTRY/$DOCKER_IMAGE:latest'
                }
            }
        }
    }
}
