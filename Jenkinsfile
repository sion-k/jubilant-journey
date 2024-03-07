/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    stages {
        stage('Run Tests') {
            steps {
                sh 'node --version'
                sh 'npm install'
                sh 'npm run build'
                sh 'npm test'
            }
        }

        stage('Image build') {
            steps {
                script {
                    docker.build("nest")
                }
            }
        }
    }
}
