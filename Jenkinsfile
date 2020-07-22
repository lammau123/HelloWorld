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
        //sshagent(['dev']) {
          steps {
            bat 'echo hello'
        //    bat '"C:\\Program Files\\Git\usr\\bin\\scp.exe" -o StrictHostkeyChecking=no target\\*.jar azureuser@13.67.119.87/home/ubuntu/dev/helloworld.jar'
          }
        }
      }
    }
  }
}
