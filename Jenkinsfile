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
        sshagent (['dev']) {
          bat 'echo hello'
          bat 'scp.exe -o StrictHostkeyChecking=no target/*.jar azureuser@52.163.241.54:/home/azureuser/dev/'
        }
      }
    }
  }
}
