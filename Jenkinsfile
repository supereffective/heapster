#!groovy
node {
	stage('Checkout'){
    checkout scm
		env.PREFIX="heapster-amd64"
  }
  stage('Build') {
		sh "make container"
  }
	stage('Push') {
    sh "eval `aws ecr get-login --no-include-email`"
		sh "docker push ${env.PREFIX}/${IMAGE_NAME}"
	}
}
