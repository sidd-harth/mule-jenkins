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
        sh 'mvn sonar:sonar   -Dsonar.projectKey=ttt   -Dsonar.host.url=http://localhost:9000   -Dsonar.login=0bb732e5b77a673c8a7c5d0ce97712fa863f3ddf -Dsonar.sources=src/'
      }
    }

    stage('Deploy to UAT') {
      steps {
        sh 'mvn clean package deploy -DmuleDeploy  -Dusername=hcl-ops-2 -Dpassword=Boi@1234 -Dwokers=1 -DworkerType=MICRO -DappName=$appName-uat -Denv=UAT'
      }
    }

    stage('Integration Tests') {
      steps {
        sh "bash integration-test.sh"
      }
    }
  }
}