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
           git credentialsId: 'jenkins-user-github', url: 'https://github.com/aakashsehgal/FMU.git'
           // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
           sh "ls -lart ./*" 
           // List all branches in your repo. 
           sh "git branch -a"
           // Checkout to a specific branch in your repo.
           sh "git checkout branchname"
          }
       }
    }
    stage('Build') {
      steps {
        dir("${env.WORKSPACE}"){
          script {
            sh """\
              mkdir -p ${GOPATH}/src/${ORG_PATH}
              rm -f ${GOPATH}/src/${REPO_PATH}
              ln -s ${env.WORKSPACE}/go/src/${REPO_PATH} ${BUILD_PATH}
              cd ${BUILD_PATH}

              make -j${nproc} -w all
              make -w extern aat
              make coverage
              make -j${nproc} dist
              make -C debian/temeva-api
            """
          }
        }
      }
    }
  }
