#!groovy
node {
	stage('Checkout'){
    checkout scm
  }
  stage('Build') {
		IMAGE_VERSION = sh(returnStdout: true, script: "git rev-list --count HEAD")
		IMAGE_NAME="${env.DOCKER_REGISTRY}/heapster:${IMAGE_VERSION}"
		sh 'OVERRIDE_IMAGE_NAME=$IMAGE_NAME:$IMAGE_VERSION make container"
  }
	stage('Push') {
    sh 'eval `aws ecr get-login --no-include-email`'
		sh 'docker push $IMAGE_NAME'
	}
}
