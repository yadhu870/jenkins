pipeline {
    agent any

    environment {
        // Define environment variables
        TOMCAT_HOST = '54.191.238.249'
        TOMCAT_PORT = '8080'
        TOMCAT_USER = 'ubuntu'

        GITHUB_REPO = 'https://github.com/yadhu870/jenkins-project.git'
    }

    stages {
        stage('Fetch Code') {
            steps {
                // Clone the GitHub repository
                git 'https://github.com/' + "${GITHUB_REPO}"
            }
        }

        stage('Build with Maven') {
            steps {
                // Build the project with Maven
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                script {
                    // Use SSH Agent to deploy to Tomcat
                    sshagent(['your_ssh_credentials']) {
                        // Copy the WAR file to the Tomcat webapps directory
                        sh "scp target/webapp.war ${TOMCAT_USER}@${TOMCAT_HOST}:/opt/tomcat/webapps/"
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}
