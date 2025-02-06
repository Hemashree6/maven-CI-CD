pipeline {
 agent any
 
 tools {
   jdk 'jdk17'
   maven '3.9.9'
 }
 stages{
     stage('checkout') {
       steps {
          checkout scm
       }
     }
     stage('build') {
       steps {
          sh "mvn clean install -DskipTests"
       }
     }
    stage('deploy') {
       steps {
        sshagent(['ssh-id']) {
      sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline/webapp/target/webapp.war ubuntu@13.60.190.28:/opt/tomcat/webapps'
     }
      }
    }
    
   }
}
