node {
    def IMAGE = "farweekz/docker_cde_mut:version-${env.BUILD_ID}"

    stage('Checkout') {
        steps {
            checkout scm
        }
    }

    stage('Build Docker Image') {
        steps {
            script {
                docker.build("$IMAGE", '.')
            }
        }
    }

    stage('Push Docker Image') {
        steps {
            script {
                docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                    docker.image(IMAGE).push('latest')
                }
            }
        }
    }

    stage('Run Docker Container') {
        steps {
            script {
                docker.image(IMAGE).run('-d --name=dockersrv -p 80:80')
            }
        }
    }
}
