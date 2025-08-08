pipeline {
    agent any
    stages {
        stage('Install') {
            steps {
                bat 'npm install'
            }
        }
        stage('Test') {
            steps {
                bat 'npm test'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-node-app:latest')
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    bat '''
                        docker stop my-node-app || true
                        docker rm my-node-app || true
                        docker run -d --name my-node-app -p 3000:3000 my-node-app:latest
                    '''
                }
            }
        }
    }
}
