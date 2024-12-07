pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        script {
          checkout scm
        }
      }
    }
    stage('List All Files After Checkout') {
      steps {
        script {
          bat 'dir C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Malak /s'
        }
      }
    }
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
          bat 'docker build -t scm-api .'
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
