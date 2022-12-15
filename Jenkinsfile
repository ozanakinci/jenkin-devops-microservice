
pipeline {
     //agent { docker { image 'node:13.8'} }
agent any 
     stages {
		stage('Build') {
			steps {	
				//sh 'node --version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
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