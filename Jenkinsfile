pipeline {
  agent {
    label 'jdk8'
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