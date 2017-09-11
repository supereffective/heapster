#!groovy
node {
	stage('Checkout'){
    checkout scm
  }
  stage('Build') {
		sh 'env'
  }
}

// sh 'OVERRIDE_IMAGE_NAME=${env.DOCKER_REGISTRY}/heapster:latest make container'
