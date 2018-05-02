// Powered by Infostretch 

timestamps {

node ('linuxslave') { 

	stage ('cjpdemo - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e7092d59-2ba1-4288-8a74-62219298460d', url: 'https://github.com/cjpcloud/jarrepo.git']]]) 
	}
	stage ('cjpdemo - Build') {
 			// Maven build step
	withMaven(maven: 'mvn') { 
 			if(isUnix()) {
 				sh "mvn clean package " 
			} else { 
 				bat "mvn clean package " 
			} 
 		}
// Unable to convert a build step referring to "com.cloudbees.dockerpublish.DockerBuilder". Please verify and convert manually if required. 
	}
	stage ('cjpdemo - Post build actions') {
/*
Please note this is a direct conversion of post-build actions. 
It may not necessarily work/behave in the same way as post-build actions work.
A logic review is suggested.
*/
// Unable to convert a post-build action referring to "hudson.plugins.s3.S3BucketPublisher". Please verify and convert manually if required.
		// Mailer notification
		step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'babu.dasp53@gmail.com', sendToIndividuals: false])
 
	}
}
}