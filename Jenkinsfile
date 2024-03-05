/* Requires the Docker Pipeline plugin */
pipeline {
    agent { 
        docker {
            image 'python:3.10-windowsservercore'
        }
    }
    stages {
        stage('build') {
            steps {
                bat 'python --version'
            }
        }
    }
}
