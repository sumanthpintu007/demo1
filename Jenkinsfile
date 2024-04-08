pipeline {
	agent any
	
	stages {
		stage ('clone') {
			steps {
			 git branch: 'master', url: 'https://github.com/druti33/demo1.git'
			}
		
		}
		stage ('compile') {
			steps {
				sh 'mvn clean install'
			}
			//post {
				//always {
					//junit 'target/surefire-reports/*.*xml'
					//archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
				}//
			}//
		}
		stage ('build image') {
			steps {
				sh 'docker build .'
			}
		
		}
	
	}
}
