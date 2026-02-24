pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'git@github.com:harishjangam235/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop devops-container || true
                docker rm devops-container || true
                docker run -d -p 8000:80 --name devops-container devops-app
                '''
            }
        }
    }
}
