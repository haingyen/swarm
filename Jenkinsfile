pipeline {
    agent {
        label 'manager-node'
    }
    environment {
        DOCKER_HUB_USER = 'haingyen'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/haingyen/swarm.git'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'docker-token', variable: 'DOCKER_HUB_TOKEN')]) {
                    sh(""" echo \$DOCKER_HUB_TOKEN | docker login -u ${DOCKER_HUB_USER} --password-stdin """, label: "login dockerhub")
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