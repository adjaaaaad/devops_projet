pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // On utilise le binaire Docker de l'hôte (lié via le volume)
                sh 'docker build -t mon-site .'
            }
        }
        stage('Deploy') {
            steps {
                dir('/var/jenkins_home/workspace/DEVOPS_pipeline') {
                    // La méthode la plus robuste : appeler docker-compose 
                    // en utilisant le chemin absolu sur l'hôte Ubuntu
                    sh '/usr/local/bin/docker-compose down || true'
                    sh '/usr/local/bin/docker-compose up -d'
                }
            }
        }
    }
}
