pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = "farweekz/docker_cde_mut:version-${env.BUILD_ID}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}", '.')
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                        docker.image("${DOCKER_IMAGE}").push()
                    }
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${DOCKER_IMAGE}").run('-d --name dockersrv -p 80:80')
                }
            }
        }
    }
}
