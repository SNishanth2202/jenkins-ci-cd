pipeline {
    agent any
    stages {
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
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
                    sh 'docker run -d --name my-node-app -p 3000:3000 my-node-app:latest || true'
                }
            }
        }
    }
}
