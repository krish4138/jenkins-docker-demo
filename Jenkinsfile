pipeline {
    agent any

    environment {
        DOCKER_HOST = 'unix:///home/krish/.docker/desktop/docker.sock'
    }

    stages {

        stage('Check Docker') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t krish-jenkins-demo:v1 .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f krish-demo || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name krish-demo -p 8085:80 krish-jenkins-demo:v1'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'docker ps'
                sh 'docker images'
            }
        }
    }
}
