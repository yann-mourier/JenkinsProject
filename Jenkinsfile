pipeline {
    agent any
    stages{
        stage('code'){
            steps{
                git url: 'https://github.com/SaurabhDahibhate/django_jenkins.git', branch: 'master'
            }
        }
        
        stage('Build'){
            steps{
                sh 'docker build . -t react-django-docker-img:latest'
            }
        }
        stage('Test'){
            steps{
                echo "Testing"
            }
        }
        stage('Deploy'){
            steps{
                sh "docker run -d --name react-django-docker-jenkins -p 8002:8002 react-django-docker-img:latest"
            }
        }
    }
}
