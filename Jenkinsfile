#!groovy

node {
    properties([
        parameters([
             stringParam(name: 'tag', defaultValue: 'latest', description: 'Tag for build'),        
             booleanParam(name: 'release', defaultValue: true, description: 'Also tag as latest')
        ])
    ])

    currentBuild.description = params.tag

    def imageName = "timoreymann/jenkins-ci-with-docker"
    def credentials = 'timoreymann-docker'
    def registry = 'https://registry.hub.docker.com'
    def app

    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        sh "docker build -t ${imageName}:${params.tag} --pull ."
    }        
   
    stage("Publish") {
        docker.withRegistry(registry, credentials) {
            if(params.tag != 'latest' || !params.release) {
                sh "docker push ${imageName}:${params.tag}"
            }
    
            if(params.release) {
                sh "docker push ${imageName}:latest"
            }
        }
    }
}
