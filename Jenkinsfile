pipeline {
    agent any
    environment {
 PATH="${PATH}:/opt/maven/bin"
}
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
            sh "ls -la"
            sh "touch abcd.txt"
        }
      }
   }
  }
 }
}