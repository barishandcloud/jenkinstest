pipeline {
  agent {
    node {
      label 'winserv1'
    }
  }
/*
  environment {
    MYHOSTNAME = ''
  }
*/
  stages {
    stage('gethostname') {
      steps {
        script {
          //echo "Print HOSTNAME Env varaible before script executed ${env.MYHOSTNAME}"
          //def result = powershell returnStdout: true, script: '[System.NET.DNS]::GetHostByName($null)'
          def result = powershell returnStdout: true, script: 'hostname' 
          print result
          stash 'result'
          //MYHOSTNAME = result
          //env.MYHOSTNAME = MYHOSTNAME
          //echo "Print HOSTNAME Env varaible after script executed ${env.MYHOSTNAME}"
        }
      }
    }
    
    stage('test var') {
      steps {
        unstash 'result'
        print result
      }
    }

    stage('createDir') {
      steps {
        powershell(script: '[system.io.directory]::CreateDirectory("c:\\test5")', returnStatus: true, returnStdout: true)
      }
    }
  }
}