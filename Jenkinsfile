pipeline {
  agent {
    node {
      label 'winserv1'
    }

  }
  stages {
    stage('gethostname') {
      script {
        def msg = powershell(returnStdout: true, script: '[System.NET.DNS]::GetHostByName($null)')
        println msg
      }
    }

    stage('createDir') {
      steps {
        powershell(script: '[system.io.directory]::CreateDirectory("c:\\test5")', returnStatus: true, returnStdout: true)
      }
    }

  }

}
