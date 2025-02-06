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
        sshagent(['ec2-ssh-credentials']) {
      sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven CI-CD/webapp/target/webapp.war ec2-user@3.88.213.212:/home/ec2-user/apache-tomcat-9.0.98/webapps'
     }
      }
    }
    
   }
}
