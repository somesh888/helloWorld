pipeline {
    agent any
    tools{
    maven 'mvn'
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
    }
}
