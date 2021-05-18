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
    stage('Upload To Nexus'){
      steps{
        script{
          def pom = readMavenPom file: 'pom.xml'
          def repository = pom.version.endsWith("SNAPSHOT") ? 'myapps-snapshot' : 'myapps-release'
          nexusArtifactUploader artifacts: 
            [[artifactId: 'myweb', classifier: '', file: "target/myweb-0.0.1.war", type: 'war']], 
          credentialsId: 'nexus3', 
          groupId: 'in.javahome', 
          nexusUrl: '172.31.0.139:8081', 
          nexusVersion: 'nexus3', protocol: 'http', 
          repository: repository, 
          version: '0.0.1'
       }
      }
    }
    
    stage('dev-deploy'){
      when {
        branch "dev"
      }
      steps{
        echo "deploy to dev environment"
      }
    }
  }
}
