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
		deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://54.248.177.169:8080/')], contextPath: 'aruntejatestpipeline', onFailure: false, war: 'target/*.war'
	}



jojoojojojmmmmmmmmmmmmmmmmmmmmmmnnnnkn

}

