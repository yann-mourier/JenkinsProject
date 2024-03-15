node {
    def IMAGE = "farweekz/docker_cde_mut:version-${env.BUILD_ID}"

    stage('Checkout') {
        checkout scm
    }

    stage('Build image') {
        docker.build("$IMAGE", '.')
    }

    stage('Test image') {
        sh "docker run -d --name testing-${env.BUILD_ID} -p 80:80 ${IMAGE}"
    }

    stage('Push image') {
        docker.build("$IMAGE", '.').push()
    }
}
