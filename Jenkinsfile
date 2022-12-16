
pipeline {
     //agent { docker { image 'node:13.8'} }
	agent any 
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:mavenHome/bin:$PATH"
	}
     stages {
		stage('Checkout') {
			steps {	
				container ('myMaven'){
				sh 'mvn --version'}
				sh 'docker version'
				echo "Build"
				echo "$PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {	
				container ('myMaven'){
				sh "mvn clean compile"}
			}
		}
		stage('Test') {
			steps {	
				container ('myMaven'){
				sh "mvn test"}
			}
		}
		stage('Integration Test') {
			steps {	
				container ('myMaven'){
				sh "mvn  failsafe:integration-test failsafe:verify"}
			}
		}
		
	}

}