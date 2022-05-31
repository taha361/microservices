pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            environment {
                 SECRET_FILE_ID = credentials('ACR')
            }
            steps {
                echo "secret file $SECRET_FILE_ID"
                sh 'az acr login --name pfacontainer --expose-token'
                //sh 'docker push containerpfa.azurecr.io/azure-vote-front:v2'
                echo 'Deploying....'
            }
        }
    }
}
