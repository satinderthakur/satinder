pipeline {
    agent any
     stages {
        stage('Docker build') {
            steps {
               bat "docker.build('demo')"
            }
        }
         stage ('Docker push') {
            steps {   
               bat "docker.withRegistry( https://506844237526.dkr.ecr.us-east-1.amazonaws.com", "ecr:us-east-1:demo-ecr-credentials")
               bat "docker.image('demo').push('latest')"
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
