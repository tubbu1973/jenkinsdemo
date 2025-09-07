pipeline {
    agent any

    stages {
        stage('Check Docker Version') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Verify') {
            steps {
                bat 'dir'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t dewixaltius/github-demo .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    bat 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                    bat 'docker push dewixaltius/github-demo'
                }
            }
        }
    }
}
