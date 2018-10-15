pipeline {
  agent {
    node {
      label 'netcore'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'dotnet restore'
        sh 'dotnet build'   
        sh 'cd coreApp.Web/bin && ls'
        zip zipFile: 'bin.zip', archive: false, dir: './coreApp.Web/bin'
      }
    }    
    stage('Test') {
      steps {
        sh 'dotnet test'
        }
      }
  }
}
