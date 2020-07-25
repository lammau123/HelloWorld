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
          bat 'scp.exe -o StrictHostkeyChecking=no target/*.jar azureuser@23.101.28.96:/home/azureuser/dev/'
          bat '''
              ssh -tt azureuser@23.101.28.96 << EOF
              java -jar ./dev/*.jar com.helloworld.test.HelloworldApplication
              exit
              EOF'''
        }
      }
    }
  }
}
