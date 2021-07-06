pipeline{
 agent any
 // tools {
 //        maven 'M2'
 //        jdk 'JDK'
 //    }

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
 	// stage ('Deploy'){
 	// 	steps {
 		
 	// 			bat 'mvn -f pom.xml package deploy  -Dusername=mule-7 -Dpassword=Qwerty67 -DmuleDeploy'
 		
 	// 	}
 	// }
 }

}