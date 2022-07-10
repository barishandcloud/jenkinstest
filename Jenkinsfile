pipeline {
  agent {
    node {
      label 'winserv1'
    }
  }

  environment {
    MYHOSTNAME = ''
  }

  stages {
    stage('gethostname') {
      steps {
        script {
          echo "Print HOSTNAME Env varaible before script executed ${env.MYHOSTNAME}"
          //def result = powershell returnStdout: true, script: '[System.NET.DNS]::GetHostByName($null)'
          def env.MYHOSTNAME = powershell returnStdout: true, script: '[System.NET.DNS]::GetHostByName($null)'
          //print result
          env.MYHOSTNAME = result
          //${env.MYHOSTNAME} = result
          echo "Print HOSTNAME Env varaible after script executed ${env.MYHOSTNAME}"
        }
      }
    }

    stage('createDir') {
      steps {
        powershell(script: '[system.io.directory]::CreateDirectory("c:\\test5")', returnStatus: true, returnStdout: true)
      }
    }
  }
}