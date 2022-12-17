
pipeline {
    //agent { docker { image 'node:13.8'} }
	agent any 
	environment {
		dockerHome = tool 'myDocker'
		//mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:mavenHome/bin:$PATH"
	}
     stages {
		stage('Checkout') {
			steps {	
				//sh 'mvn --version'
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
				sh "docker version clean compile"
			}
		}
		stage('Test') {
			steps {	
				sh "docker version test"
			}
		}
		stage('Integration Test') {
			steps {	
				sh "docker version failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package') {
			steps {	
				sh "docker version package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps {	
				//docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG
				script {
					docker.build("docker build -t ozanakinci/repotest:tagname:$env.BUILD_TAG")
				}
			}
		}
		stage('Push Docker Image') {
			steps {	
				script {
					docker.withRegistry('', 'dockerhub'){
						docker.Image.push();
						docker.Image.push('latest');
				}
			  }
			}
		}
		
	}

}