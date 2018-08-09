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
        stage('Test') {
          steps {
            sh 'echo \'Test\''
          }
        }
      }
    }
    stage('Should you') {
      steps {
        script {
          somevalue = input(message: 'Should you package', id: 'somevalue', ok: 'true')
        }

      }
    }
    stage('Speak') {
      steps {
        script {
          echo "${somevalue}"
          if("${somevalue}" == "true") {
            echo 'Hello, bitwiseman!'
            sh 'echo \'hit the speak message\''
          }
        }

      }
    }
  }
  environment {
    PATH = "/usr/local/bin:$PATH"
  }
}