#!groovy
node {
	stage('Checkout'){
    checkout scm
		IMAGE_NAME="heapster-amd64"
  }
  stage('Build') {
		env.PREFIX=env.DOCKER_REGISTRY
		sh "make container"
  }
	stage('Push') {
    sh "eval `aws ecr get-login --no-include-email`"
		sh "docker push ${env.PREFIX}/${IMAGE_NAME}"
	}
}
