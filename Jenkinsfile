pipeline {
  agent {
    node {
      label 'winserv1'
    }

  }
  stages {
    stage('gethostname') {
      steps {
        powershell(script: '[System.NET.DNS]::GetHostByName($null)', returnStatus: true, returnStdout: true)
      }
    }

  }
}