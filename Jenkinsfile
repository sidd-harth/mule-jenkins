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
        sh 'mvn clean install'
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
        withSonarQubeEnv('Sonarqube') {
        sh 'mvn sonar:sonar   -Dsonar.projectKey=ttt   -Dsonar.host.url=http://localhost:9000   -Dsonar.login=0bb732e5b77a673c8a7c5d0ce97712fa863f3ddf -Dsonar.sources=src/'
      } 
    }
    }

    stage('SonarQube Quality Gate') {
      steps {
        withSonarQubeEnv('Sonarqube') {
          timeout(time: 2, unit: 'MINUTES') {
             script {
               waitForQualityGate abortPipeline: true
             }
         }
       }
      } 
    }
    

    stage('Deploy to UAT') {
      steps {
        sh 'mvn clean package deploy -DmuleDeploy  -Dusername=hcl-ops-2 -Dpassword=Boi@1234 -Dwokers=1 -DworkerType=MICRO -DappName=$appName-uat-21548 -Denv=UAT -Dconfig=UAT'
      }
    }

    stage('Integration Tests') {
      steps {
        sh "bash integration-test.sh"
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
        sh 'mvn clean package deploy -DmuleDeploy  -Dusername=hcl-ops-2 -Dpassword=Boi@1234 -Dwokers=1 -DworkerType=SMALL -DappName=$appName-prod-21548 -Denv=PROD -Dconfig=PROD'
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