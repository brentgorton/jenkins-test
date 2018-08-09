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
          doPackage = input(message: 'Should you package', id: 'doPackage')
          echo "${doPackage}"
        }

      }
    }
    stage('Speak') {
      when {
        expression {
          doPackage == 'Proceed'
        }

      }
      steps {
        echo 'Hello, bitwiseman!'
        sh 'echo \'hit the speak message\''
      }
    }
  }
  environment {
    PATH = "/usr/local/bin:$PATH"
    doPackage = 'false'
  }
}