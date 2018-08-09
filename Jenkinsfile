pipeline {
  agent any
  stages {
    stage('Environment Setup') {
      steps {
        sh 'npm install grunt grunt-cli'
      }
    }
    stage('Execute') {
      steps {
        sh 'grunt echo'
      }
    }
  }
  environment {
    PATH = "/usr/local/bin:$PATH"
  }
}