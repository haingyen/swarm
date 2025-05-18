pipeline {
    agent {
        label 'manager-node'
    }
    environment {
        SWARM_MANAGER_IP = '54.255.224.226'
        SSH_CREDS = credentials('jenkins-swarm-access')
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/haingyen/swarm.git'
            }
        }
        stage('Deploy Stack') {
            steps {
                    sh "docker stack deploy -c docker-compose.yml myapp"
            }
         }
    }
}