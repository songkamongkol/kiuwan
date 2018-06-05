pipeline {
  agent {
    label 'jdk9'
  }
  stages {
    stage('Say Hi') {
      steps {
        echo 'Hi World!'
        sh 'java -version'
      }
    }
  }
}