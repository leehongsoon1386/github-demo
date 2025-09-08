// Updated Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Verify') {
            steps {
                sh 'ls -al'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t leejason1386/github-demo .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%'
                    sh 'docker push leejason1386/github-demo'
                }
            }
        }
    }
}
