// Powered by Infostretch 

timestamps {

node () {

	stage ('App-IC - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git-login', url: 'https://github.com/Mdidier1821/jenkins-sample']]]) 
	}
	stage ('App-IC - Clean') {
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn clean" 
			} else { 
 				bat "mvn clean" 
			} 
 		} 
	}
	stage ('App-IC - Build') {
	withMaven(maven: 'maven') { 
 			if(isUnix()) {
 				sh "mvn package" 
			} else { 
 				bat "mvn package" 
			} 
 		} 
	}
	stage('Quality check') {
	withSonarQubeEnv('Sonar') {
		bat "mvn sonar:sonar"
	        }
	}
}
}
