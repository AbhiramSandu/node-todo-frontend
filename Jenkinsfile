pipeline {
 environment {
  registry = 'venkat/microservices-node-todo-frontend'
  registryCredential = 'dockerhub'
  dockerImage = ''
  containerId = sh(script: 'docker ps -aqf "name=node-app", returnStdout:true)
  }
  agent any
  tools {
   noodjs "node"
  }

  Stages {
   stage('Cloning project') {
    git 'https://github.com/gustavoapolinario/node-todo-frontend'
   }
   stage('Build') {
    sh 'npm install'
   }
   stage('Test') {
    sh 'npm test'
   }
   stage('Building image') {
    stpes {
     script {
      dockerImage = docker.build registry + ":$BUILD_NUMBER"
     }
    }
   }
  }
}
        /*docker.withRegistry( 'https://' + registry, registryCredential ) {
		    def buildName = registry + ":$BUILD_NUMBER"
			newApp = docker.build buildName
			newApp.push()
        }
	}
	stage('Registring image') {
        docker.withRegistry( 'https://' + registry, registryCredential ) {
    		newApp.push 'latest2'
        }
	}
    stage('Removing image') {
        sh "docker rmi $registry:$BUILD_NUMBER"
        sh "docker rmi $registry:latest"
    }
    
}*/
