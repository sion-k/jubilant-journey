/* Requires the Docker Pipeline plugin */
pipeline {
    agent { 
        docker {
            image 'henriqueholtz/node-win:16.15.1'
        }
    }
    stages {
        stage('build') {
            steps {
                bat 'node --version'
            }
        }
    }
}
