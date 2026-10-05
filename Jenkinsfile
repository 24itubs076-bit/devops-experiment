pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dockerpipeline .'
            }
        }

        stage('Run Test Container') {
            steps {
                sh 'docker run -d --name dockerpipeline-test -p 3001:3000 dockerpipeline'
            }
        }

        stage('Test Application') {
            steps {
                sh 'curl http://host.docker.internal:3001'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker stop dockerpipeline-test || true'
                sh 'docker rm dockerpipeline-test || true'
            }
        }
    }
}