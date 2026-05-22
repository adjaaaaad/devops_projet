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
    }
}
