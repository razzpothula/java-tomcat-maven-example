pipeline
node{
stage('SCM Checkout'){
git url :'https://github.com/razzpothula/java-tomcat-maven-example.git'
}
  stage('Compile the code'){
    def mvnhome = tool name: 'mvn', type: 'maven'
    sh "${mvnhome}/bin/mvn compile"
  }
  stage('Package the code'){
    def mvnhome = tool name: 'mvn', type: 'maven'
    sh "${mvnhome}/bin/mvn package"
  }
  stage('Deploy to tomcat server'){
    sshagent(['tomcat-deploy']) {
      sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkinsfile_project/target/*.war ubuntut@13.234.136.208:/opt/tomcat/webapps'
    } 
  }

  

