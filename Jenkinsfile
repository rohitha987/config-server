pipeline {	
	agent any	tools {	    
		maven 'my-maven’		
		jdk 'my-jdk’	
	}	
	stages {        
		stage('Clone'){			
			steps {git url:'https://github.com/rohitha987/config-server.git', branch:'main’}			}		
		stage('Build'){			
			steps {bat "mvn clean install -DskipTests"}		
		}		
		stage('Test'){			
			steps{bat "mvn test"}		}		
		}
		stage('Deploy') {			
			steps { bat "docker build -t config-image ."			    
			            bat "docker run -p 8088:8088 -d --name config-container config-image"}		
		}		
	}
}
