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
        sh 'dotnet test --no-build --no-restore'
        }
      }
  }
}
