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
             echo "PATH = " ${PATH}
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
        withCredentials([azureServicePrincipal(credentialsId: '714f096c-9d39-46fc-a56c-600b3c7964b9',
                                    subscriptionIdVariable: 'ARM_SUBSCRIPTION_ID',
                                    clientIdVariable: 'ARM_CLIENT_ID',
                                    clientSecretVariable: 'ARM_CLIENT_SECRET',
                                    tenantIdVariable: 'ARM_TENANT_ID')]) {
          bat '''
            echo " AZUre = " %ARM_CLIENT_ID%
            echo " AZUre = " %ARM_TENANT_ID%
            echo " AZUre = " %ARM_CLIENT_SECRET%
            echo " AZUre = " %ARM_SUBSCRIPTION_ID%
            terraform init -input=false
            terraform plan -out=tfout -input=false
            terraform apply tfout -input=false
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
