node(){

	
	stage('Code Checkout'){
		checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubCreds', url: 'https://github.com/arunteja-prog/MavenBuild.git']])
	}
	stage('Build Automation'){
		sh """
			ls -lart
			mvn clean install
			ls -lart target
		"""
	}
	

	stage('Code Deployment'){
		deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://35.77.201.137:8080/')], contextPath: 'harishtestpipeline', onFailure: false, war: 'target/*.war'
	}

	stage('email notification'){
		mail bcc: '', body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>""", cc: 'harishchalluri@gmail.com', from: '', replyTo: '', 
		subject: 'Test Application Notification', to: 'arunteja195@gmail.com'
		
}
}

