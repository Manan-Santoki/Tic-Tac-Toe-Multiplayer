pipeline {
  agent any
  environment {

    registry = "raptor1702/game"
    registryCredential = 'dockerhub'
  }

  stages {
    stage('Get Source'){
        steps{
            checkout scm
        }
    }
    stage('Docker Build') {
      agent any
      steps {
        script {
          dockerImage = docker.build registry + ":latest"
        }
      }
    }
    stage('Push Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push()
          }
        }
      }
    }
  }
}