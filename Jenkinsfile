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
             set TEST = %PATH%
             echo "TEST = " %TEST%
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
        withCredentials([azureServicePrincipal('714f096c-9d39-46fc-a56c-600b3c7964b9')]) {
          bat '''
            set ARM_CLIENT_ID = %AZURE_CLIENT_ID% 
            set ARM_CLIENT_SECRET = %AZURE_CLIENT_SECRET% 
            set ARM_TENANT_ID = %AZURE_TENANT_ID%
            set ARM_SUBSCRIPTION_ID = %AZURE_SUBSCRIPTION_ID%
            echo " AZUre = " %ARM_CLIENT_ID%
            echo " AZUre = " %ARM_TENANT_ID%
            echo " AZUre = " %ARM_CLIENT_SECRET%
            echo " AZUre = " %ARM_SUBSCRIPTION_ID%
            terraform init -input=false
            terraform plan -out=tfout -input=false
            terraform apply tfout -auto-approve -input=false
          '''
        }
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
