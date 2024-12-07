pipeline {
  agent any
  stages {
    stage('Clean') {
      steps {
        script {
          bat 'dotnet clean SCM.sln'
        }
      }
    }
    stage('Restore') {
      steps {
        script {
          bat 'dotnet restore SCM.sln'
        }
      }
    }
    stage('Build') {
      steps {
        script {
          bat 'dotnet build SCM.sln'
        }
      }
    }
    stage('Docker Build') {
      steps {
        script {
          bat 'docker build scm-api .'
        }
      }
    }
    stage('Deploy to Staging') {
      steps {
        script {
          bat 'docker-compose up --build -d'
        }
      }
    }
  }
}
