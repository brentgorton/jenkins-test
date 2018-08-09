pipeline {
  agent none
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
    stage('Should you package') {
      steps {
        input(ok: 'true', id: 'somevalue', message: 'Want to package')
      }
    }
    stage('package') {
      when {
        expression {
          params.somevalue == 'true'
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