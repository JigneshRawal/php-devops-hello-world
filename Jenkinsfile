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
                sh 'docker login azacreufirst.azurecr.io --username $ACR_LOGIN --password $PASS'
                sh 'docker images'
            }
            }
        }
        stage("Publish-Images"){
            steps{
                sh 'docker build -t azacreufirst.azurecr.io/php-devops-hello-world:php -f Dockerfile . --disable-content-trust'
                sh 'docker push azacreufirst.azurecr.io/php-devops-hello-world:php'
            }
        }
    }
}