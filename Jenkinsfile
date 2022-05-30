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
                sh './testfile.sh'
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl get services'
                echo 'Deploying....'
            }
        }
    }
}
