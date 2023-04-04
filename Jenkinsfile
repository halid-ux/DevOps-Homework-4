pipeline {
    agent {
        docker {
            image 'docker:stable'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t halid99/jenkins-docker-1 .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: '4ac996dc-ff7f-4198-a83a-5729d4e86dff', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                    sh 'docker push halid99/jenkins-docker-1'
                }
            }
        }
    }
}

