pipeline {
  agent any
  stages {
    stage('Environment Setup') {
      steps {
        sh '''npm install grunt grunt-cli
exit 0'''
      }
    }
    stage('Execute') {
      parallel {
        stage('Execute') {
          steps {
            sh 'grunt echo'
          }
        }
        stage('') {
          steps {
            sh 'echo \'Test\''
          }
        }
      }
    }
  }
  environment {
    PATH = "/usr/local/bin:$PATH"
  }
}