/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Image build') {
            steps {
                sh 'docker build -t nest .'
                sh 'docker stop nest'
                sh 'docker rm nest'
                sh 'docker run -d -p 3000:3000 --name nest nest'
            }
        }
    }
}
