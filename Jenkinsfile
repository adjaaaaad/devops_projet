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
                    // Les commandes sh DOIVENT être à l'intérieur de steps
                    sh 'docker stop mon-site-container || true'
                    sh 'docker rm mon-site-container || true'
                    sh 'docker run -d --name mon-site-container -p 80:80 mon-site'
                }
            }
        }
        stage('Moniteur') {
            steps {
                echo 'Monitoring : Vérification de la disponibilité...'
                sh 'sleep 2'
                sh 'curl -f http://192.168.1.22:80 || { echo "ALERTE : Le site ne répond pas !"; exit 1; }'
                
                echo 'Monitoring : Analyse des performances du conteneur...'
                // Affiche la consommation CPU et RAM en temps réel
                sh 'docker stats mon-site-container --no-stream'
            }
        }
    }
}
