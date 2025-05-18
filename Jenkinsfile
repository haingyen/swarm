pipeline {
    agent any
    environment {
        SWARM_MANAGER_IP = '54.255.224.226'
        SSH_CREDS = credentials('swarm-ssh-acess')
    }
    stages {
        stage('Deploy Stack') {
            steps {
                sshagent([SSH_CREDS]) {
                    sh """
                        ssh -o StrictHostKeyChecking=no ubuntu@${SWARM_MANAGER_IP} \
                        "docker stack deploy -c docker-compose.yml myapp"
                    """
                }
            }
        }
    }
}