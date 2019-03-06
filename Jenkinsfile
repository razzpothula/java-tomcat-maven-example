pipeline
node{
stage('SCM Checkout'){
git url :'https://github.com/razzpothula/java-tomcat-maven-example.git'
}
  stage('Compile the code'){
    def mvnhome = tool name: 'mvn', type: 'maven'
    sh "${mvnhome}/bin/mvn compile"
  }
  stage('Sonarqube Analysis'){
    def mvnhome = tool name: 'mvn', type: 'maven'
    withSonarQubeEnv('sonar-5'){
      sh "${mvnhome}/bin/mvn sonar:sonar"
    }
  }
  stage('Package the code'){
    def mvnhome = tool name: 'mvn', type: 'maven'
    sh "${mvnhome}/bin/mvn package"
  }
  stage('Email Notifications'){
    mail bcc: '', body: '''To check the email
Notification
Thanks
rajesh''', cc: '', from: '', replyTo: '', subject: 'jenkins jobs', to: 'rajeshpothula.bj@gmail.com'
  }
}

