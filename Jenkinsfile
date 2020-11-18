pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				//git '/home/JenkinsDependencyCheckTest'
				git 'https://github.com/derektan1801/JenkinsDependencyCheckTest'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
