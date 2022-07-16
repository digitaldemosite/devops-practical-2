pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/digitaldemosite/devops-practical-2.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t devopsclass:latest .' 
                sh 'docker tag devopsclass manojt777/devopsclass:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
        withDockerRegistry([ credentialsId: "DockerHub", url: "" ]) {
           sh  'docker push manojt777/devopsclass:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
