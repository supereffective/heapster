#!groovy
node {
	stage('Checkout'){
    checkout scm
		env.PREFIX=env.DOCKER_REGISTRY
    sh "eval `aws ecr get-login --no-include-email`"
  }
  stage('Build heapster') {
		IMAGE_NAME="heapster-amd64"
		sh "make container"
  }
	stage('Push heapster') {
		sh "docker push ${env.PREFIX}/${IMAGE_NAME}"
	}
	stage('Build heapster-influxdb') {
		IMAGE_NAME="heapster-influxdb-amd64"
		sh "cd influxdb && make container"
  }
	stage('Push heapster-influxdb') {
		sh "docker push ${env.PREFIX}/${IMAGE_NAME}"
	}
	stage('Build heapster-grafana') {
		IMAGE_NAME="heapster-grafana-amd64"
		sh "cd grafana && make container"
  }
	stage('Push heapster-grafana') {
		sh "docker push ${env.PREFIX}/${IMAGE_NAME}"
	}
}
