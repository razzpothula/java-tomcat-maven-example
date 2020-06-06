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
    }
   
  

