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
        stage('Monitor') {
            steps {
                echo 'Monitoring : Vérification de l\'état du site...'
                // On utilise curl pour vérifier que le serveur répond avec le code 200 (OK)
                sh 'curl -f http://localhost:80 || { echo "ALERTE : Le site ne répond pas !"; exit 1; }'
                echo 'Monitoring : Le site est opérationnel !'
            }
        }
    }
}
