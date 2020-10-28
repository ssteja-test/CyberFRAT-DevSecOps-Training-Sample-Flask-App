pipeline {
  environment {
    registry = "8019733984/cyberfrat-devsecops"
    registryCredential = "DockerHubKey"
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
    
    stage('push to DockerHub') {
      steps {
        script {
          docker.withRegistry('', registryCredential ) { 
            dockerImage.push()
          }
        }
      }
    }
    
    stage ('Test Run') {
      steps {
        sh 'docker run -d $registry:$BUILD_NUMBER'
      }
    }
  }
}
