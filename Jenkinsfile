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
                sh 'docker push containerpfa.azurecr.io/azure-vote-front:v2'
                echo 'Deploying....'
            }
        }
    }
}
