node {
    def IMAGE = "farweekz/docker_cde_mut:version-${env.BUILD_ID}"

    stage('Checkout') {
        checkout scm
    }
    
    stage('Test image') {
        sh "docker run -d --name web -p 80:80 nginx"
    }
}
