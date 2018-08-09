pipeline {
  agent any
  stages {
    stage('Environment Setup') {
      parallel {
        stage('Environment Setup') {
          steps {
            sh '''npm config set //registry.npmjs.org/:_authToken $npmtoken
npm install grunt grunt-cli
exit 0'''
          }
        }
        stage('root npm install') {
          steps {
            sh '''npm config set //registry.npmjs.org/:_authToken $npmtoken
npm install'''
          }
        }
        stage('angular npm install') {
          steps {
            sh '''npm config set //registry.npmjs.org/:_authToken $npmtoken
cd angular && npm install'''
          }
        }
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
  npmtoken = '38282b02-2ad5-4869-80bb-c9771fcc7cf1'
}
}