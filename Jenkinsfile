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
        //archiveArtifacts artifacts: 'CoreApp.Web/bin/Debug/netcoreapp2.1/**', fingerprint: true
      }
    }    
    stage('Test') {
      steps {
        sh 'dotnet test CoreApp.Tests/CoreApp.Tests.csproj --no-build --no-restore'
      }
    }
    stage('Publish') {
      steps {
        sh 'dotnet publish -c Release'
        //sh 'cd CoreApp.Web/bin/Debug/netcoreapp2.1/publish && ls'
        sh 'sudo zip -r ./CoreApp.Web/bin/Release/netcoreapp2.1/release_publish.zip ./CoreApp.Web/bin/Release/netcoreapp2.1/publish/**'
      }
    }
  }
  post {
    always {
        //archiveArtifacts artifacts: 'CoreApp.Web/bin/Debug/netcoreapp2.1/*.*', fingerprint: true
        archiveArtifacts artifacts: 'CoreApp.Web/bin/Release/netcoreapp2.1/release_publish.zip', fingerprint: true
    }
  }
}
