pipeline {
    agent any

    stages {
        stage('git clone') {
            steps {
               git 'https://github.com/yadhu870/jenkins-project.git'
            }
        }
        stage('bulid') {
            steps {
               sh "mvn clean package"
        }
    }
    stage('deploy') {
    steps {
        script {
        sshagent(['9eaadda4-0431-4c92-b269-eb067861375f']) {
            sh 'scp target/webapp.war ubuntu@54.221.126.124:/opt/tomcat/webapps/'
        }
      }
   }
  }
 }
}