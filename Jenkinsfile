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
                dir('/var/jenkins_home/workspace/DEVOPS_pipeline') {
                    // On utilise 'docker compose' via le binaire docker déjà partagé
                    // Si 'docker compose' ne fonctionne pas, on utilise le plugin intégré
                    sh 'docker compose down || docker-compose down'
                    sh 'docker compose up -d || docker-compose up -d'
                }
            }
        }
    }
}
