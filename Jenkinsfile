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
        input(message: 'Should you package', id: 'somevalue', ok: 'true')
      }
    }
    stage('Speak') {
      when {
        expression {
          '${somevalue}' == 'true'
        }

      }
      steps {
        echo 'Hello, bitwiseman!'
      }
    }
  }
  environment {
    PATH = "/usr/local/bin:$PATH"
  }
}