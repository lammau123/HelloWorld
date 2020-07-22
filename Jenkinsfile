pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  stages {
    stage('Initialize') {
      steps {
        bat '''
             echo Initialzie 
             echo "PATH = " %PATH%
             echo "M2_HOME = " %M2_HOME%
            '''
      }
    }
    stage ('Build') {
      steps {
        bat 'mvn clean package'
      }
    }
    stage ('Deploy to Dev') {
      steps {
        sshagent('[dev]') {
          steps {
            bat '"C:\\Program Files\\Git\usr\\bin\\scp.exe" -i "c:\\Users\\tom\\.ssh\\azure\\id_rsa" C:\\Users\\tom\\.jenkins\\workspace\\scp-to-linux\\abc.jar tom@xy.xyz.xy.xz:abc.jar'
          }
        }
      }
    }
  }
}
