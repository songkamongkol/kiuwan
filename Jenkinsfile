pipeline {
  agent { node { label 'kiuwan' } }

  options {
    buildDiscarder(logRotator(numToKeepStr: "10"))
    disableConcurrentBuilds()
    timestamps()
  }

  stages {
    stage('Checkout') {
      steps {
        script {
           // The below will clone your repo and will be checked out to master branch by default.
           git credentialsId: 'boon: 'https://github.com/SpirentOrion/orion-api.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // List all branches in your repo. 
           sh "git branch -a"
          }
       }
    }
    stage('Build') {
      steps {
        dir("${env.WORKSPACE}"){
          script {
            sh """\
              echo "hello"
            """
          }
        }
      }
    }
  }
