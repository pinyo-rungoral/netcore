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
        sh 'dotnet build --no-restore'   
        sh 'cd CoreApp.Web/bin/Debug/netcoreapp2.1 && ls'
         archiveArtifacts artifacts: './CoreApp.Web/bin/Debug/netcoreapp2.1/*.dll', fingerprint: true
      }
    }    
    stage('Test') {
      steps {
        sh 'dotnet test CoreApp.Tests/CoreApp.Tests.csproj --no-build --no-restore'
        }
      }
  }
  post {
    always {
        archiveArtifacts artifacts: './CoreApp.Web/bin/Debug/netcoreapp2.1/*.*', fingerprint: true
    }
  }
}
