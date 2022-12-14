//agent { docker:latest { image 'maven:3.6.3'} }
pipeline{
  agent any
	stages {
		stage('Build') {
			steps {	
				//sh 'mvn --version'
				echo "Build"
			}
		}
		stage('Test') {
			steps {	
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {	
				echo "Integration Test"
			}
		}

		post {
			always {
				echo 'I run awesome.I run always'
			}
			success {
				echo 'I run when you are successful'
			}
			failure {
				echo 'I run when you fail'
			}
		}
		
	}
}

