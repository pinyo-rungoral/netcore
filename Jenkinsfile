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
       
      }
    }    
    stage('Test') {
      steps {
        sh 'dotnet test'
        }
      }
  }
}
