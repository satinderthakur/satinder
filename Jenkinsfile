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
               bat "docker login -u AWS https://506844237526.dkr.ecr.us-east-1.amazonaws.com"
               bat "Password:India@123
               bat "docker push 506844237526.dkr.ecr.us-east-1.amazonaws.com/demo:latest"
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
