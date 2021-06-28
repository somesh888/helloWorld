/*
properties = null

def loadProperties() {
    node {
        cleanWs()
        checkout scm
        properties = readJSON file: "properties.json"
        echo "Product Properties File: properties.json"
        //loadProperties ()
    }
}
*/

pipeline {
    agent any //{label "${properties.gem5k.nodeLabels}"}
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '15', numToKeepStr: '5')
    }
    parameters {
        choice choices: ['gem5k', 'mars', 'chemstat'], description: 'select product type!', name: 'productType'
        choice choices: ['testBuild', 'devBuild', 'releaseBuild'], description: 'The specific type of build desired. devBuild is a standard nightly build, testBuild is a non-incrementing build, A releaseBuild removes the IUO flag from the build.', name: 'buildType'
    }
    stages {
        stage('prep') {
            steps {
                script {
                    //loadProperties()
                    //def productType = "${productType}"
                    properties = readJSON file: 'properties.json'
                    echo "${properties.gem5k.pollTime}"
                    echo "${buildType}"
                }
            }
        }
        stage('cleanup') {
            steps {
                cleanWs()
            }
        }
    }
}