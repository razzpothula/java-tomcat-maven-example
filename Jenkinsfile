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
    stage("publissh to Nexus-artifact-uploader"){
    nexusArtifactUploader artifacts: [[artifactId: 'java-tomcat-maven-example', classifier: '', file: 'target/hello Maven Webapp-1.0.war', type: 'war']], 
      credentialsId: 'Nexus-Repository-Manager', 
      groupId: 'com.example',
      nexusUrl: '18.221.137.168:8081',
      nexusVersion: 'nexus3', 
      protocol: 'http', 
      repository: 'Nexus-user', 
      version: '1.0'
    }
      }
    
   
  

