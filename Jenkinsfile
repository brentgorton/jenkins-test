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
            sleep 60
          }
        }
        stage('Test') {
          steps {
            sh 'echo \'Test\''
            sleep 60
          }
        }
      }
    }
  }
  environment {
    PATH = "/usr/local/bin:$PATH"
  }
}