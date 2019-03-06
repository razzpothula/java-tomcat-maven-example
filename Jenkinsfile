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
    sshagent(['new-deploy']){
      sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/cicdpipeline/target/*.war ubuntut@13.127.65.33:/opt/tomcat/webapps'
    } 
  }
}

  

