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
          env.doPackage = input(message: 'Should you package', id: 'doPackage')
        }

      }
    }
    stage('Speak') {
      steps {
        script {
          echo "${env.doPackage}"
          if("${doPackage}" == "Ok") {
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