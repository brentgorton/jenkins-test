pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        withNPM(npmrcConfig: 'npmrc')
      }
    }
  }
}