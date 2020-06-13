pipeline
  node{
    stage("SCM Checkout"){
      //add to github url through declarative syntax
     git credentialsId: 'username', url: 'https://github.com/razzpothula/java-tomcat-maven-example.git'
    }
      stage('Compile'){
            //Get maven home path
            def mvnhome = tool name: 'mvn', type: 'maven'
            sh "${mvnhome}/bin/mvn compile"
        }
    stage('Package'){
            def mvnhome = tool name: 'mvn', type: 'maven'
            sh "${mvnhome}/bin/mvn package"
  }
    stage('Sonarqube') {
    environment {
        def mvnhome = tool 'sonar'
    }
  }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
  }
    
    
    
  

