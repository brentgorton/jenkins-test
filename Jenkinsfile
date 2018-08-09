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
          description:'describing choices', name:'nameChoice', choices: "Cutting Edge\nMaster"]
        ])
        echo "${doPackage}"
      }

    }
  }
  stage('Deploy to Master') {
    when {
      expression {
        doPackage == 'Master'
      }

    }
    steps {
      echo 'Deploying to Master'
    }
  }
  stage('Deploy to Cutting Edge') {
    when {
      expression {
        doPackage == 'Cutting Edge'
      }

    }
    steps {
      echo 'Deploying to Cutting Edge'
    }
  }
}
environment {
  PATH = "/usr/local/bin:$PATH"
  doPackage = 'false'
}
}