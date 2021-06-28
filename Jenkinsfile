pipeline {
    agent any //{label "${properties.gem5k.nodeLabels}"}
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '15', numToKeepStr: '5')
    }
    parameters {
        choice choices: ['gem5k.json', 'mars.json', 'chemstat.json'], description: 'select product type!', name: 'productType'
    }
    stages {
        stage('prep') {
            steps {
                script {
                    properties = readJSON file: "${productType}"
                    echo "properties file: ${productType}"
                    echo "${properties.pollTime}"
                }
            }
        }
        stage('cleanup') {
            steps {
                echo "${properties.product_config}"
                cleanWs()
            }
        }
    }
}