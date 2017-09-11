#!groovy
node {
	stage('Checkout'){
    checkout scm
  }
  stage('Build') {
		sh 'OVERRIDE_IMAGE_NAME=$DOCKER_REGISTRY/heapster:latest make container'
  }
}
