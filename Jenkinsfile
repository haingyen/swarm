pipeline {
    agent {
        label 'manager-node'
    }
    environment {
        DOCKER_HUB_CREDS = credentials('docker-hub-creds') 
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/haingyen/swarm.git'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                script {
                    sh "echo ${DOCKER_HUB_CREDS_PSW} | docker login -u ${DOCKER_HUB_CREDS_USR} --password-stdin"
                }
            }
        }
        stage('Deploy Stack') {
            steps {
                    sh "docker run --name reactjs-app -d -p 80:80 haingyen/reactjs-app:v1"
            }
         }
    }
}