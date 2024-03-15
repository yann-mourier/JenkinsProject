node {
    def IMAGE = "farweekz/docker_cde_mut:version-${env.BUILD_ID}"

    stage('Checkout') {
        git 'https://github.com/yann-mourier/JenkinsProject.git'
    }

    stage('Test image') {
        sh "docker help"
    }

    stage('Build image') {
        docker.build("$IMAGE", '-f Dockerfile .')
    }


    stage('Test image') {
        sh "docker run -d --name testing-${env.BUILD_ID} -p 80:80 ${IMAGE}"
    }

    stage('Push image') {
        docker.build("$IMAGE", '.').push()
        sh "docker run -d --name web -p 80:80 nginx"
    }
}
