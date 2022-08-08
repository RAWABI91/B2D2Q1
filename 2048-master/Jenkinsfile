pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('rawabi-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t rawabim/2048:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push rawabim/2048:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
