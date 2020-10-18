pipeline {
  agent any
  
  stages {
    stage('Build DockerImage') {
      steps {
        sh 'docker build -t cyberfrat:$BUILD_NUMBER .'
    }
   }
  }
 }
