pipeline {
  agent any
  environment {
    PATH = "/usr/local/bin:/opt/homebrew/bin:${PATH}"
    DOCKER_HOST = "unix:///Users/joginalee/.docker/run/docker.sock"
  }
  stages {
    stage('Verify') {
      steps {
        sh 'ls -al'
      }
    }
    stage('Build Docker Image') {
      steps {
        sh 'docker version'          // sanity check
        sh 'docker build -t leehongsoon1386/github-demo .'
      }
    }
    stage('Push Docker Image') {
      when {
        expression { return sh(script: 'command -v docker >/dev/null 2>&1', returnStatus: true) == 0 }
      }
      steps {
        // withDockerRegistry([credentialsId: 'dockerhub-creds']) { docker.image('...').push('latest') }
        echo 'Push step placeholder'
      }
    }
  }
}
