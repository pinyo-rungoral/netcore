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
      }
    }    
    stage('Test') {
      steps {
        echo 'dotnet test'
        }
      }
  }
}
