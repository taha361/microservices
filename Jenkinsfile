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
                sh 'docker-compose down'
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker tag mcr.microsoft.com/azuredocs/azure-vote-front:v1 containerpfa.azurecr.io/azure-vote-front:v2'
                sh 'docker push containerpfa.azurecr.io/azure-vote-front:v2'
                echo 'Deploying....'
            }
        }
    }
}
