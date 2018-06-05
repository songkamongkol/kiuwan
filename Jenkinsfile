pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hi') {
      steps {
        echo "Hi World ${MY_NAME}!"
        sh 'java -version'
      }
    }
  }
  environment {
    MY_NAME = 'Boon'
  }
}