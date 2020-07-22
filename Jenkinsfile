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
             echo %PATH%
             echo %M2_HOME%
            '''
      }
    }
  }
}
