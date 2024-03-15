node {
    docker.image('nginx:latest').withRun('-P 80:80') { c ->
        sh 'docker ps'
        sh 'curl localhost'
    }
}
