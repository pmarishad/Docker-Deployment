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

	// Renaming the build 
	stage('Renaming'){
		sh "mv target/*.war target/myapp.war"
	}

	// Creating the Docker Image from Dockerfile
	stage('Docker_Image_Creation'){
		def dockerImage = "docker build -t pmarishad/myapp:v1.0 ."
		sh "${dockerImage}"
	}

	// Docker push
	stage('Docker_Push_to_DockerHub'){
		withCredentials([string(credentialsId: 'dockerHub', variable: 'dockerLogin')]) {
    	// some block
    	sh "docker login -u pmarishad -p ${dockerLogin}"
    	echo "Login Success..!"
    	sh 'docker push pmarishad/myapp:v1.0'
		}

	}
}
