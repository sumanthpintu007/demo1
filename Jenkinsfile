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
                sh 'docker build -t imagename .'
            }
        }
        stage ('push image') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhubid', variable: 'dockerpwd')]) {
                        sh "docker login -u priya668 -p ${dockerpwd}"
                        sh 'docker push imagename'
                    }
                }
            }
        }
    }
}
