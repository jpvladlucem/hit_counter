pipeline{
	agent any
  
	environment {
		DOCKERHUB_CREDENTIALS=credentials('28a5c9e9-6014-4736-b66f-f1ce5773a2d5')
	}

	stages {
		stage('Build') {
			steps {
				sh 'docker build -t jpvl/hit_counter .'
			}
		}

		stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {
			steps {
				sh 'docker push jpvl/hit_counter:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
