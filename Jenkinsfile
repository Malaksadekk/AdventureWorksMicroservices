pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          sh 'dotnet build SCM.sln'
        }
      }
    }
    stage('Docker Build') {
      steps {
        script {
          sh 'docker build -t scm-api .'
        }
      }
    }
    stage('Deploy to Staging') {
      steps {
        script {
          sh 'docker-compose up --build -d'
        }
      }
    }
  }
}