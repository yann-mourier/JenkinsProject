pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t farweekz/docker_cde_mut:1.0 .'
            }
        }
        
        stage('Push Docker Image') {
            steps {
                sh 'sudo docker push farweekz/docker_cde_mut:1.0'
            }
        }
        
        stage('Run Docker Container') {
            steps {
                sh 'sudo docker run -d --name=dockersrv -p 80:80 farweekz/docker_cde_mut:1.0'
            }
        }
    }
}
