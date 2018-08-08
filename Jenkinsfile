pipeline {
  agent any
  stages {
    stage('test') {
      steps {
        node(label: 'test') {
          sh 'npm install'
        }

      }
    }
  }
}