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
      bat 'mvn clean package'
    }
  }
}
