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
       sh "docker build -t harsha59/myapp:v1 ."
      }
    }
    
    stage('push to docker hub'){
       steps{
          withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerPwd')]){
              sh "docker login -u harsha59 -p ${dockerPwd}"
              sh "docker push harsha59/myapp:v1"
         }
       }
    }
    stage('dev-deploy'){
      steps{
         echo "deploy to dev environment"
      }
    }
  }
}
