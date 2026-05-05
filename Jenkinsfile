pipeline {
    agent any

    environment {
        IMAGE_NAME = "sanjay5raj/my-app:latest"
        CONTAINER_NAME = "my-node-container"
        PORT = "3000"
    }

    stages {

        stage('Pull Docker Image') {
            steps {
                sh "docker pull $IMAGE_NAME"
            }
        }

        stage('Stop Old Container') {
            steps {
                sh """
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                """
            }
        }

        stage('Run Container') {
            steps {
                sh """
                docker run -d -p $PORT:3000 --name $CONTAINER_NAME $IMAGE_NAME
                """
            }
        }

    }

    post {
        success {
            echo "App deployed successfully 🚀"
        }
        failure {
            echo "Deployment failed ❌"
        }
    }
}