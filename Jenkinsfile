pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '/usr/bin/docker build -t mon-site .'
            }
        }
        stage('Deploy') {
            steps {
                dir('/var/jenkins_home/workspace/DEVOPS_pipeline') {
                    sh '/usr/bin/docker compose down || true'
                    sh '/usr/bin/docker compose up -d'
                }
            }
        }
    }
}
