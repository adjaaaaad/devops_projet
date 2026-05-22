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
                // On se place directement dans le dossier
                dir('/var/jenkins_home/workspace/DEVOPS_pipeline') {
                    // On appelle docker-compose sans le -f, car il trouvera automatiquement le fichier docker-compose.yml
                    sh 'docker-compose down || true'
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}
