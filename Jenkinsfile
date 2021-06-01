pipeline{
  agent any

  tools{
    maven 'Maven3'
  }
  
  stages{
    stage('Maven Build'){
      steps{
        sh "mvn clean package"
      }
    }
    stage('Docker Build Image'){
      steps{
       sh "docker build . -t harsha59/myapp:v1"
      }
    }
    
    stage('push to docker hub'){
      
      steps{
        echo "deploy to dev environment"
      }
    }
    stage('dev-deploy'){
      steps{
         echo "deploy to dev environment"
      }
    }
  }
}
