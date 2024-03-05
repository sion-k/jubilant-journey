pipeline{
    agent any

    environment {
       CONTAINER_NAME="health"
       NAME = "health"
       VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
       GIT_URL="https://github.com/sion-k/jubilant-journey.git"
    }

    stages {
        stage('Pull') {
            steps {
                git url:"${GIT_URL}", branch:"main", poll:true, changelog:true
            }
        }

        stage('Clean'){
            steps{
                script {
                    try {
                        sh "docker stop ${CONTAINER_NAME}"
                        sleep 1
                        sh "docker rm ${CONTAINER_NAME}"
                    } catch (e) {
                        sh 'exit 0'
                    }
                }
            }
        }

        stage('Build') {
            steps {
                sh "docker build -t ${NAME} ."
            }
        }

        stage('Deploy'){
            steps {
                sh "docker tag ${NAME}:latest ${NAME}:${VERSION}"
                sh "docker run -d --name=${CONTAINER_NAME} -p 8000:8000 ${NAME}:latest"
            }
        }
    }
}