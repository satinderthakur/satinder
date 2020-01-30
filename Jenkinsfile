pipeline {
    agent any
     stages {
        stage('Build') {
            steps {
                bat "Invoke-Expression -Command (Get-ECRLoginCommand -Region us-east-1).Command"
                bat "docker build -t demo ."
            }
        }
         stage ('Docker push') {
            steps {   
               bat "docker tag demo:latest 506844237526.dkr.ecr.us-east-1.amazonaws.com/demo:latest"
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
