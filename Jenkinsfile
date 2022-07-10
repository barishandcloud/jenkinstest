def myhostname = 'I do not know the host name'

pipeline {
  agent {
    node {
      label 'winserv1'
    }
  }

  stages {
    stage('1 - gethostname') {
      steps {
        echo "Print myhostname Env varaible before script executed ${myhostname}"
        script {          
          //def result = powershell returnStdout: true, script: '[System.NET.DNS]::GetHostByName($null)'
          def result = powershell returnStdout: true, script: 'hostname' 
          println "hostname info within script block: ${result}"
          myhostname = result.trim()
          //stash 'result'
          echo "Print myhostname Env varaible within script in stage 1 ${myhostname}"
        }
      }
    }
    
    stage('2 - test var') {
      steps {
        echo "Print myhostname Env varaible within steps in stage 2 ${myhostname}"
      }
    }

    stage('3 - createDir') {
      steps {
        powershell(script: '[system.io.directory]::CreateDirectory("c:\\test5")', returnStatus: true, returnStdout: true)
      }
    }
  }
}