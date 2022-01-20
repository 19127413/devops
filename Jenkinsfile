pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('19127413_docker')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/19127413/devops.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t 19127413/docker:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push 19127413/docker:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
