pipeline {
    agent any

    environment {
        DOCKER_REGISTRY = 'Tspringer1204' // Replace with your Docker Hub username
        DOCKER_IMAGE = 'tariq-docker-image'           // Replace with your image name
    }

    stages {
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

