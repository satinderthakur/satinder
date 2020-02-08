pipeline {
    agent any
     stages {
        stage('Docker build') {
            steps {
               bat "docker build -t demo ."
            }
        }
         stage ('Docker push') {
            steps {   
               bat "docker login" 
               bat "docker push https://hub.docker.com/repositories", "docker-hub-credientials" 
            }
        }     
        stage('Test') {
            steps {
                bat "mvn test"
            }
        }
        stage('Deploy') {
            steps {
                bat "mvn package"
            }
        }
    }
}
