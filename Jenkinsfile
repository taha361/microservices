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
                sh 'docker-compose up -d'
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl'
                echo 'Deploying....'
            }
        }
    }
}
