pipeline {
  agent {
    node {
      label 'netcore'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'dotnet restore'
      }
    }
  }
}
