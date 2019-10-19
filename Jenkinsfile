node{
	
	// SCM checkout from gitHub
	stage('SCM_Checkout'){
		git 'https://github.com/pmarishad/Docker-Deployment.git'
	}

	// Building war file using Maven
	stage('Build'){
		def mvnHome = tool name: 'Maven-Home', type: 'maven'
		def mvnCmd = "${mvnHome}/bin/mvn"
		sh "${mvnCmd} clean package"
		echo "Build has been Done...!"
	}

}
