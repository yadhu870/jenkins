pipeline {
 agent any
 environment {

  PATH="${PATH}:/opt/apache-maven-3.6.3/bin"
 }
 stages {
 stage('Git Clone') {
 steps {
 git branch: 'master', credentialsId: 'GitHub-Credentials',
url: 'https://github.com/yadhu870/jenkins-test.git'
 }
 }

 stage('Maven Build') {
 steps {
 sh "mvn clean package"
 }
 }
 stage("deploy to tomcat"){
     steps{
         sshagent(['a4a074d6-0481-4476-a01a-1b36f1829f1e']) {
     sh 'scp -o StrictHostKeyChecking=no target/webapp.war root@18.246.37.78:/opt/tomcat/webapps/'
}
     }
 }

 }
}
