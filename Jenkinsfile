pipeline {
  agent any
  environment {
    DOCKERHUB_USER = "sondossoua"
    PATH = "C:\\Users\\sondo\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin;${env.PATH}"
  }
  stages {
    stage('Build') {
      steps {
        bat "docker build -t mern-server ./Server"
        bat "docker build -t mern-client ./Client"
      }
    }
    stage('Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'U', passwordVariable: 'P')]) {
          bat "docker login -u %U% -p %P%"
          bat "docker tag mern-server %DOCKERHUB_USER%/mern-server:latest"
          bat "docker tag mern-client %DOCKERHUB_USER%/mern-client:latest"
          bat "docker push %DOCKERHUB_USER%/mern-server:latest"
          bat "docker push %DOCKERHUB_USER%/mern-client:latest"
        }
      }
    }
    stage('Deploy') {
      steps {
        bat "docker rm -f client server mongodb"
        bat "docker compose up --build -d"
      }
    }
    stage('Test') {
      steps {
        bat "ping -n 8 127.0.0.1 > nul"
        bat "curl -f http://localhost:9000/api/health"
      }
    }
  }
}