#!groovy
node {
    properties([
        parameters([
            gitTagVersionInput()
        ])
    ])

    runDefaultDockerPipeline currentBuild: currentBuild, imageName: "timoreymann/jenkins-ci-with-docker", tag: params.Version
}
