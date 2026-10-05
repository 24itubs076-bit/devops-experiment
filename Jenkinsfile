pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t dockerpipeline .'
            }
        }

        stage('Run Test Container') {
            steps {
                bat 'docker run -d --name dockerpipeline-test -p 3001:3000 dockerpipeline'
            }
        }

        stage('Test Application') {
            steps {
                bat 'curl http://localhost:3001'
            }
        }

        stage('Cleanup') {
            steps {
                bat 'docker stop dockerpipeline-test'
                bat 'docker rm dockerpipeline-test'
            }
        }
    }
}