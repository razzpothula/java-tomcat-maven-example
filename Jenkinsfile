pipeline
  node{
    stage("SCM Checkout"){
      //add to github url through declarative syntax
     git credentialsId: 'username', url: 'https://github.com/razzpothula/java-tomcat-maven-example.git'
    }
      stage('Package'){
            def mvnhome = tool name: 'mvn', type: 'maven'
            sh "${mvnhome}/bin/mvn package"
   }
    stage('deploy to atrifacts'){
    }
        nexusArtifactUploader artifacts: [[artifactId: 'java-tomcat-maven-example', classifier: '', file: 'target/', type: 'war']], 
          credentialsId: 'nexus-user-credentials', 
          groupId: 'com.example',
          nexusUrl: ' 13.59.190.104:8081/', 
          nexusVersion: 'nexus3', 
          protocol: 'http', 
          repository: 'Jenkin-User', 
          version: '1.0-SNAPSHOT'

   } 
}
   
  

