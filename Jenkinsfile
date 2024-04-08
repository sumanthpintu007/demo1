pipeline {
	agent any
	
	stages {
		stage ('clone') {
			steps {
			 git branch: 'master', url: 'https://github.com/adikarthik/demo1.git'
			}
		
		}
		stage ('compile') {
			steps {
				sh 'mvn clean install -DskipTests'
			}
		}
		stage ('build image') {
			steps {
				sh 'docker build .'
			}
		
		}
	
	}
}
