pipeline {
    agent any
     stages {
        stage('Build') {
            steps {
                bat "docker build -t demo ."
            }
        }
         stage ('Docker push')
            docker.withRegistry('https://1234567890.dkr.ecr.us-east-1.amazonaws.com', 'ecr:us-east-1:demo-ecr-credentials') {
               docker.image('demo').push('latest')
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
