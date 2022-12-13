pipeline {
	//agent any
	agent { docker:latest { image 'maven:3.6.3'} }
	stages {
		stage('Build') {
			steps {	
				sh 'mvn --version'
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
		
	}
}

