pipeline {
   agent any 
   environment {
	DOCKER_HUB_CREDENTIALS = credentials('docker-hub-credentials')
   }
   stages{
	stage('Clone Repository'){
	   steps{
	       git branch: 'master', url: 'https://github.com/sansdongre/todoapplication.git'
           }
        }
	stage('builds with maven'){
           steps{
               sh 'mvn clean package -Dskiptests'
           }
        }
	stage('Build Docker Image'){
           steps{
               sh 'docker build -t todo-applicatopn-myimage:latest .'
           }
        }
	stage('Push Image to Docker Hub'){
           steps{
                sh 'docker login -u sansdongre -p S@nskruti100298
	      	sh 'docker tag todo-application-myimage:latest sansdongre/todo-aplication-myimage:latest'
		sh 'docker push sansdongre/todo-aplication-myimage:latest
           }
        }
	stage('Verify Services'){
	   steps{
		sh 'docker ps'
	   }
	}
	stage('Clean workplace'){
           steps{
                sh 'rm -rf *'
           }
        }
   }
   post{
   	success{
   		echo 'Build and deployment successful'
   	}
   	failure{
   		echo 'Build and deployment failed'
   	}
   }
}
      

	
