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
        script{
          zip archive: true, dir: './CoreApp.Web/bin/Debug/netcoreapp2.1', glob: '', zipFile: 'debug.zip'
        }
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
        archiveArtifacts artifacts: './CoreApp.Web/bin/**/*.*', fingerprint: true
    }
  }
}
