pipeline {
  agent {
    node {
      label 'winserv1'
    }

  }
  stages {
    stage('gethostname') {
      steps {
        powershell '[System.NET.DNS]::GetHostByName($null)'
      }
    }

  }
}