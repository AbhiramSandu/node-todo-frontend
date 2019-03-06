pipeline {
 environment {
  registry = 'venkat/microservices-node-todo-frontend'
  registryCredential = 'dockerhub'
  dockerImage = ''
  containerId = sh(script: 'docker ps -aqf "name=node-app", returnStdout:true')
  }
  agent any
  tools {
   noodjs "node"
  }

  stages {
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
       
