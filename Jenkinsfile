pipeline {
    agent any
    stages{
            stage("Build"){
                steps{
                    echo "Hi this is build stage"
                }
            }
            stage("Docker Login"){
            steps {
           withCredentials([usernamePassword(credentialsId: 'ACRLOGIN', passwordVariable: 'PASS', usernameVariable: 'ACR_LOGIN')]) {
                sh 'docker login azacreufirst.azureacr.io --username $ACR_LOGIN --password $PASS'
                sh 'docker images'
            }
            }
        }
}