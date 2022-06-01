pipeline {
    agent any

    stages {
        stage('Azure Login') {
                 AzureCredentials = credentials('AzureAccount')
            }
            steps {
                sh 'az  login -u $AzureCredentials_USR -p $AzureCredentials_PSW '
                echo 'Login In..'
            }
        }
        stage('Build Docker Images') {
            steps {
                sh 'docker build -t containerpfa.azurecr.io/azure-vote-front ./azure-vote'
                echo 'Building..'
            }
        }
        stage('Push Docker Images to ACR') {
            steps {
                sh 'az acr login --name containerpfa'
                sh 'docker push containerpfa.azurecr.io/azure-vote-front:latest'
                echo 'pushing..'
            }
        }
        stage('Deploy to AKS') {
            steps {
                //sh 'az aks get-credentials --resource-group kubernetesgroup --name pfaaks'
                //sh 'az aks update -n pfaaks -g kubernetesgroup --attach-acr containerpfa'
                sh 'kubectl apply -f azure-vote-all-in-one-redis.yaml'
                sh 'kubectl set image deployment azure-vote-front azure-vote-front=containerpfa.azurecr.io/azure-vote-front:latest'
                
                echo 'Deploying...'
            }
        }
    }
}
