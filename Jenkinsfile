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
            // On utilise 'docker compose' (version moderne)
            // On précise le chemin complet du fichier avec l'option -f
            sh 'docker compose -f /var/jenkins_home/workspace/DEVOPS_pipeline/docker-compose.yml up -d --build'
        }
    }
    }
}
