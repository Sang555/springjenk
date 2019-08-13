pipeline {
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
   withDockerRegistry('dockerhub','') {
      // following commands will be executed within logged docker registry
       def customImage = docker.build("my-image:${env.BUILD_ID}")
       customImage.push()
   }
        }
    }
}
