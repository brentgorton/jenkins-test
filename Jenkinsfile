pipeline {
  agent {
    docker {
      image '9-alpine'
    }

  }
  stages {
    stage('test') {
      steps {
        sh '''npm install
grunt echo'''
      }
    }
  }
}