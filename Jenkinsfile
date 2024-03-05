/* Requires the Docker Pipeline plugin */
pipeline {
    agent { 
        docker {
            image 'python:3.10-windowsservercore'
            label 'windows' // Optional label to ensure the agent runs on a Windows node
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
