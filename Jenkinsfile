#!groovy
node {
	stage('Checkout'){
    checkout scm
  }
  stage('Build') {
		def version = sh (returnStdout: true, script: 'git rev-list --count HEAD')
		sh 'OVERRIDE_IMAGE_NAME=$DOCKER_REGISTRY/heapster:${version} make container'
  }
}
