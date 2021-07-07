pipeline {
  agent any

  tools {
    maven 'M363'
  }

  environment {
    appName = "hello-devops"
    cloudhubRegion = "us-e2"
    cloudhubHost = "cloudhub.io"
    port = "80"
  }

  stages {

    stage('Build Artefact') {
      steps {
        sh 'echo OK'
      }
    }

    stage('MUnit Testing') {
      steps {
        //sh 'mvn test'
        sh 'echo MUnit Testing is Success'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        sh 'echo OK'
      }
    }

    stage('Deploy to UAT') {
      steps {
        sh 'echo OK'
      }
    }

    stage('Integration Tests') {
      steps {
        sh "echo OK"
      }
    }

    stage('Prompte to PROD?') {
      steps {
        timeout(time: 2, unit: 'DAYS') {
          input 'Do you want to Approve the Deployment to Production Environment?'
        }
      }
    }

    stage('Deploy to PROD') {
      steps {
        sh 'echo OK'
      }
    }

    stage('Integration Tests - PROD') {
      steps {
        sh 'echo Integration Testing is Success'
      }
    }

    stage('Smoke Tests - PROD') {
      steps {
        sh 'echo Smoke Testing is Success'
      }
    }
    
    stage('Stress Tests - PROD') {
      steps {
        sh 'echo Stress Testing is Success'
      }
    }

  }
}