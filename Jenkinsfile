pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh 'docker rmi -f $(docker images -q) || true'
                        sh "docker build -t basha999/node-app:v$BUILD_NUMBER ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push basha999/node-app:v$BUILD_NUMBER "
                    }
                }
            }
        }
    }
}
