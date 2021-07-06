pipeline{
 agent any
 tools {
        maven 'M363'
    }

 stages {
  //  stage('Check Parameters') {
  //  steps {
  //   echo "Production App Name - ${username}"
  //   echo "Application Name - ${password}"

  //  }
  // }
 	stage ('Build'){
 		steps {
 		
 				sh 'mvn clean install'
 		
 		}
 	}


  stage ('SonarQube'){
    steps {
    
        sh 'mvn sonar:sonar   -Dsonar.projectKey=ttt   -Dsonar.host.url=http://localhost:9000   -Dsonar.login=0bb732e5b77a673c8a7c5d0ce97712fa863f3ddf -Dsonar.sources=src/'
    
    }
  }
  
 	stage ('Deploy'){
 		steps {
 		
 				sh 'mvn clean package deploy -DmuleDeploy  -Dusername=hcl-ops-2 -Dpassword=Qwerty67 -Dwokers=1 -DworkerType=MICRO -DappName=test123sidasd -Denv=Sandbox'
 		
 		}
 	}
 }

}