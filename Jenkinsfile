node{
   stage('SCM Checkout'){
     git 'https://github.com/devopscloud4/Devops.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
    stage('Deploy to Tomcat'){
    sshagent(['tomcat-user']) {
    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/warpipeline/target/myweb-0.0.1.war ec2-user@172.31.27.37:/opt/apache-tomcat-8.5.35/webapps/'
   }
   }
}


/*pipeline {
     agent any
	 tools {
        maven 'maven'
	}
	stages {
	    stage("clone code"){
		    steps{
			   git 'https://github.com/devopscloud4/Devops.git'
			}
		stage("build code"){
		  steps{
		     sh "mvn clean install"
			 {
		}
		    stage('Deploy to Tomcat'){
            sshagent(['tomcat-user']) {
			sh 'scp -r StrictHostKeyChecking=no /var/lib/jenkins/workspace/war pipeline/target/myweb-0.0.1.war ec2-user@172.31.27.37:/opt/apache-tomcat-8.5.35/webapps/'
		    }
		}*/
