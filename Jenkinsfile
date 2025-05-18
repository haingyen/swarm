pipeline {
    agent {
        label 'manager-node'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/haingyen/swarm.git'
            }
        }
        stage('Deploy Stack') {
            steps {
                    sh "docker-compose up -d"
            }
         }
    }
}