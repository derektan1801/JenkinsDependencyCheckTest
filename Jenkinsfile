pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				step([$class: 'WsCleanup'])
				cleanWs()
				checkout scm
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
