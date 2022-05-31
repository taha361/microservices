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
                 AzureCredentials = credentials('AzureAccount')
            }
            steps {
                echo "secret file $AzureCredentials"
                sh 'az  login -u tahayassine.benameur@insat.u-carthage.tn -p Iphone3gs '
                sh 'az acr login --name containerpfa'
                //sh 'docker push containerpfa.azurecr.io/azure-vote-front:v2'
                echo 'Deploying....'
            }
        }
    }
}
