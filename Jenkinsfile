pipeline {
  agent {
    node {
      label 'winserv1'
    }

  }
  stages {
    stage('gethostname') {
      steps {
        powershell(script: '[System.NET.DNS]::GetHostByName($null)', returnStatus: true)
      }
    }

    stage('createDir') {
      steps {
        powershell(script: '[system.io.directory]::CreateDirectory("c:\\test5")', returnStatus: true, returnStdout: true)
      }
    }

  }
}