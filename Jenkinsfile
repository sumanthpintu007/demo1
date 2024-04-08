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
                withCredentials([usernamePassword(credentialsId: '1be70791-bfcf-49e6-8bdf-e41c2c72ad66', passwordVariable: 'Priya123456', usernameVariable: 'priya668')]) {
                    sh 'echo $Priya123456 | docker login -u $priya668 --password-stdin'
                }
                sh 'docker push imagename'
            }
        }
    }
}
