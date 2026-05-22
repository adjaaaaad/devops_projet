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
                    sh '/usr/local/bin/docker-compose down'
                    sh '/usr/local/bin/docker-compose up -d'
                }
            }
        }
    }
}
