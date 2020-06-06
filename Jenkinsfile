pipeline
  node{
    stage("SCM Checkout"){
      //add to github url through declarative syntax
      git 'https://github.com/razzpothula/java-tomcat-maven-example.git'
    }
    stage('Package'){
            def mvnhome = tool name: 'mvn', type: 'maven'
            sh "${mvnhome}/bin/mvn package"
        }
    stage("Publish to Nexus-Repositoty-Manager")
    steps{
      nexusArtifactUploader credentialsId: 'nexus-user-credentials',
        groupId: 'nexus',
        nexusUrl: '18.188.234.88:8081/',
        nexusVersion: 'nexus2',
        protocol: 'http', 
        repository: 'Maven 2',
        version: '3.23'
    }
    }
   
  

