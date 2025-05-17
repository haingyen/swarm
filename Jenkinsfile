pipeline {
    agent any
    environment {
        SWARM_MANAGER_IP = '10.0.0.121'
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
        
        stage('Verify Deployment') {
            steps {
                sshagent([SSH_CREDS]) {
                    sh """
                        ssh ubuntu@${SWARM_MANAGER_IP} \
                        "docker service ls | grep myapp"
                    """
                }
            }
        }
    }
}