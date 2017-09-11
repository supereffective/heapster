#!groovy
node {
	stage('Checkout'){
    checkout scm
		IMAGE_NAME="${env.DOCKER_REGISTRY}/heapster"
		IMAGE_VERSION = sh(returnStdout: true, script: "git rev-list --count HEAD")
		env.OVERRIDE_IMAGE_NAME="${IMAGE_NAME}:${IMAGE_VERSION}"
  }
  stage('Build') {
		sh "make container"
  }
	stage('Push') {
    sh "eval `aws ecr get-login --no-include-email`"
		sh "docker push ${IMAGE_NAME}"
	}
}
