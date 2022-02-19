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
                cp webapp/target/webapp.war  /home/ubuntu/apache-tomcat-9.0.56/webapps
                /home/ubuntu/apache-tomcat-9.0.56/bin/startup.sh
                """
            }   
        }
    }
}
