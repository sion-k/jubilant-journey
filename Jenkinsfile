/* Requires the Docker Pipeline plugin */
pipeline {
    agent none
    stages {
        agent { docker { image 'node:20.11.1-alpine3.19' } }
        stage('Run Tests') {
            steps {
                sh 'node --version'
                sh 'npm install'
                sh 'npm run build'
                sh 'npm test'
            }
        }

        agent any
        stage('Image build') {
            steps {
                script {
                    docker.build("nest")
                }
            }
        }
    }
}
