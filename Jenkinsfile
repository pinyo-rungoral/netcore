pipeline {
  agent {
    node {
      label 'netcore'
    }

  }
  stages {
    stage('Restore Nuget') {
      steps {
        sh 'dotnet restore'
      }
    }
    stage('Build') {
      steps {
        sh 'dotnet build'
      }
    }
  }
}
