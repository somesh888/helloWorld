pipeline {
    agent any
    tools{
    maven 's_maven'
    }
    stages {
        stage('build') {
            steps { 
                sh """
                mvn -version
                mvn clean package
                """
            }
        }
        stage('deploy') {
            steps {
                sh """
                cp webapp/target/webapp.war  /home/jenkins/tomcat/apache-tomcat-9.0.58/webapps
                /home/jenkins/tomcat/apache-tomcat-9.0.58/bin/startup.sh
                """
            }   
        }
    }
}