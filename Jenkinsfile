pipeline {
  agent {
    node {
      label 'winserv1'
    }
  }
  
  stages {
    stage('gethostname') {
      steps {
		    script {
			    def result = powershell returnStdout:true, script: '[System.NET.DNS]::GetHostByName($null)'
			    print result
          env.MYHOSTNAME = result
          echo "Print HOSTNAME Env varaible ${env.MYHOSTNAME}"
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