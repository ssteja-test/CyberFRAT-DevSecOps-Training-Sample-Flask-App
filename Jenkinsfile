pipeline {
  environment {
    registry = "8019733984/cyberfrat-devsecops"
    registryCredential = "docker hub key"
    dockerImage = ''
  }
  agent any
  
  stages {
    stage('Build DockerImage') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
          }
        }
      }
    
    stage('push to dockerhub') {
      steps {
        script {
          docker.withRegistry('', registryCredential ) { 
            docker.Image.push()
          }
        }
      }
    }
    
    stage ('Test Run') {
      steps {
        sh 'docker run -d cyberfrat:$BUILD_NUMBER'
      }
    }
  }
}
