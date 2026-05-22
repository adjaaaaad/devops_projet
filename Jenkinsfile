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
            sh 'docker-compose -f /var/jenkins_home/workspace/DEVOPS_pipeline/docker-compose.yml up -d --build'
        }
    }
    }
}
