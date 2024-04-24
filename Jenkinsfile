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
         sshagent(['ad41e07e-900a-4778-b639-40616aaca8df']) {
     sh 'scp -o StrictHostKeyChecking=no target/webapp.war root@35.91.144.46:/opt/tomcat/webapps/'
}
     }
 }

 }
}
