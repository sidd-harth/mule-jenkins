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
 	stage ('Deploy'){
 		steps {
 		
 				sh 'mvn clean package deploy -DmuleDeploy  -Dusername=hcl-ops-2 -Dpassword=Qwerty67 -Dwokers=1 -DworkerType=MICRO -DappName=test123sidasd -Denv=Sandbox'
 		
 		}
 	}
 }

}