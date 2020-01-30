pipeline {
    agent any
     stages {
        stage('Build') {
            steps {
                bat "docker build -t demo ."
            }
        }
         stage ('Docker push')
            docker tag demo:latest 506844237526.dkr.ecr.us-east-1.amazonaws.com/demo:latest
            docker push 506844237526.dkr.ecr.us-east-1.amazonaws.com/demo:latest
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
