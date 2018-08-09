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
          doPackage = input(id: 'userInput', message: 'Merge to?',
          parameters: [[$class: 'ChoiceParameterDefinition', defaultValue: 'strDef',
          description:'describing choices', name:'nameChoice', choices: "QA\nUAT\nProduction\nDevelop\nMaster"]
        ])
        echo "${doPackage}"
      }

    }
  }
  stage('Speak') {
    when {
      expression {
        doPackage == 'Master'
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