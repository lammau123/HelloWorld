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
 /*   stage ('scan git'){
      steps {
        bat 'rm trufflehog || true'
        bat 'docker run gesellix/trufflehog --json https://github.com/lammau123/HelloWorld.git > trufflehog'
        bat 'cat trufflehog'
      }
    }
    stage ('Build') {
      steps {
        bat 'mvn clean package'
      }
    }*/
    stage ('Create infra') {
      steps {
        bat 'terraform init -input=false'
        bat 'terraform plan -out=tfout -input=false'
        bat 'terraform apply tfout -auto-approve -input=false'
      }
    }
    /*
    stage ('Deploy to Dev') {
      steps {
        sshagent (['dev']) {
          bat 'echo hello'
          bat 'scp.exe -o StrictHostkeyChecking=no target/*.jar azureuser@13.76.41.57:/home/azureuser/dev/'
          bat '''
              ssh -tt azureuser@13.76.41.57 < start.sh
              '''
        }
      }
    }*/
  }
}
