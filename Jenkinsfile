pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('roba-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t robaalmehmadi/runaway-game:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push robaalmehmadi/runaway-game:latest'
			}
		}
	}

	stage {
		always {
			sh 'docker logout'
		}
	}

}