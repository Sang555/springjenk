pipeline {
      environment {
    registry = "sanvs/spring-demo"
    registryCredential = ‘dockerhub’
  }
    agent any
    stages {
        stage('---clean---') {
            steps {
                sh "mvn clean"
            }
        }
        stage('--test--') {
            steps {
                sh "mvn test"
            }
        }
        stage('--package--') {
            steps {
                sh "mvn package"
            }
        }
        stage('Build image') {
            steps {
                script{
   docker.build registry + ":$BUILD_NUMBER"
                }
        }
    }
        
    }
}
