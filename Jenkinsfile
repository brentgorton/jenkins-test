pipeline {
  agent {
    docker {
      image 'node/9-alpine'
    }

  }
  stages {
    stage('error') {
      steps {
        withNPM(npmrcConfig: '6b413fd8-8261-4b35-b97c-51e071c3afbc') {
          sh '''export PATH=$PATH:/usr/local/bin
npm install grunt grunt-cli
grunt echo'''
        }

      }
    }
  }
}