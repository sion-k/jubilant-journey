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
                script {
                    docker.build("nest")
                    docker.image("nest").stop()
                    docker.image("nest").remove()
                    docker.run("nest")
                }
            }
        }
    }
}
