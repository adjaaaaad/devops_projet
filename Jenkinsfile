pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t mon-site .'
            }
        }
        stage('Deploy') {
            steps {
                // On demande à l'hôte (via docker.sock) de lancer la commande
                // Cela contourne totalement le manque de docker-compose dans Jenkins
                sh 'docker exec -u 0 mon-projet-final_jenkins_1 docker compose -f /var/jenkins_home/workspace/DEVOPS_pipeline/docker-compose.yml down || true'
                sh 'docker exec -u 0 mon-projet-final_jenkins_1 docker compose -f /var/jenkins_home/workspace/DEVOPS_pipeline/docker-compose.yml up -d'
            }
        }
    }
}
