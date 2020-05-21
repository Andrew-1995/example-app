node {
	def app

	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = sh label: '', script: 'sudo docker build -t test1 .'
	}

	stage('Test') {
		app.inside {
			sh 'npm test'
		}
	}

	stage('Push image') {
		docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
			app.push('latest')
		}
	}
}

