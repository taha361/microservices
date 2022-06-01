pipeline {
    agent any

    stages {
        stage('Azure Login') {
            steps {
                sh 'az  login -u tahayassine.benameur@insat.u-carthage.tn -p Iphone3gs '
                echo 'Login In..'
            }
        }
        stage('Build Docker Images') {
            steps {
                sh 'sudo chmod 666 /var/run/docker.sock'
                sh 'docker build -t containerpfa.azurecr.io/azure-vote-front ./azure-vote'
                //sh 'docker-compose down'
                echo 'Building..'
            }
        }
        stage('Push Docker Images to ACR') {
            steps {
                sh 'az acr login --name containerpfa'
                //sh 'docker tag mcr.microsoft.com/azuredocs/azure-vote-front:v1 containerpfa.azurecr.io/azure-vote-front:v2'
                //sh 'az acr repository delete --name containerpfa --image azure-vote-front:v3 --yes'
                sh 'docker push containerpfa.azurecr.io/azure-vote-front:latest'
                //sh 'docker rmi containerpfa.azurecr.io/azure-vote-front:v3'
                echo 'pushing..'
            }
        }
        stage('Deploy to AKS') {
            environment {
                 AzureCredentials = credentials('AzureAccount')
            }
            steps {
                //echo "secret file $AzureCredentials"
                sh 'az aks get-credentials --resource-group kubernetesgroup --name pfaaks'
                //sh 'az aks update -n pfaaks -g kubernetesgroup --attach-acr containerpfa'
                sh 'kubectl apply -f azure-vote-all-in-one-redis.yaml'
                sh 'kubectl set image deployment azure-vote-front azure-vote-front=containerpfa.azurecr.io/azure-vote-front:latest'
                
                echo 'Deploying...'
            }
        }
    }
}
