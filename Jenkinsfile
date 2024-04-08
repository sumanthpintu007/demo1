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
                sh 'docker build -t your_image_name .'
                withCredentials([usernamePassword(credentialsId: '1be70791-bfcf-49e6-8bdf-e41c2c72ad66', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                }
                sh 'docker push your_image_name'
            }
        }
    }
}

