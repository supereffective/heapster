#!groovy
node {
	stage('Checkout'){
    checkout scm
  }
  stage('Build') {
		sh 'env'
		def version = sh (returnStdout: true, script: 'git rev-list --count HEAD')
		sh 'OVERRIDE_IMAGE_NAME=$DOCKER_REGISTRY/heapster:${version} make container'
  }
}
