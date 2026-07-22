pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh 'docker build -t gentyala/services:v1 /src/'
            }
        }
         stage('Push image to dockerHub') {
            steps {
              script{
                  withDockerRegistry(credentialsId: 'docker-cred') {
                  sh 'docker push gentyala/services:v1'
                }
              }
            }
        }
    }
}
