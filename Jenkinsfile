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
  stage("Quality Gate status"){
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
      }        
  stage('Package the code'){
    def mvnhome = tool name: 'mvn', type: 'maven'
    sh "${mvnhome}/bin/mvn package"
  }
  stage('Deploy to tomcat server'){
    sshagent(['new-deploy']){
      sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/cicdpipeline/target/*.war ubuntut@13.127.65.33:/home/ubuntu'
    } 
  }
  stage('Email Notifications'){
    mail bcc: '', body: '''To check the email
Notification
Thanks
rajesh''', cc: '', from: '', replyTo: '', subject: 'jenkins jobs', to: 'rajeshpothula.bj@gmail.com'
  }
}

