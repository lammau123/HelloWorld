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
        withCredentials([azureServicePrincipal('714f096c-9d39-46fc-a56c-600b3c7964b9')]) {
          bat 'az login --service-principal -u %AZURE_CLIENT_ID% -p %AZURE_CLIENT_SECRET% -t %AZURE_TENANT_ID%'
         // bat 'terraform init -input=false'
         // bat 'terraform plan -out=tfout -input=false'
         // bat 'terraform apply tfout -auto-approve -input=false'
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
