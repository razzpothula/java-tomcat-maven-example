pipeline
node {
stage('Scm Checkout'){
url :'https://github.com/razzpothula/java-tomcat-maven-example.git'
}
  stage('Compile'){
   //Get maven home path
    def mvnhome = tool name: 'mvn-3.2', type: 'maven'
     sh "${mvnhome}/bin/mvn compile"
  }
}
