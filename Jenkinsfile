pipeline {
  agent { node { label 'kiuwan' } }
  stages {
    stage('Checkout') {
      steps {
        dir("${env.WORKSPACE}/orion-api"){
          script {
             // The below will clone your repo and will be checked out to master branch by default.
             git credentialsId: 'orion-api', url: 'git@github.com:SpirentOrion/orion-api.git'
             // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
             sh "ls -lat ./*" 
             // List all branches in your repo. 
             sh "git branch -a"
          }
        }
      }
    }
    stage('Build') {
      steps {
        dir("${env.WORKSPACE}"){
          kiuwan applicationName: 'AION', connectionProfileUuid: 'Hez5-9srI', failureThreshold: 40.0, sourcePath: './orion-api', timeout: 1440, unstableThreshold: 90.0
        }
      }
    }
  }
}
