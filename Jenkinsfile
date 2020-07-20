pipeline {
  environment {
    registry = "abhijeet7963/testapp"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
  stages {
     stage('Initialize'){
        def dockerHome = tool 'myDocker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
    }
    stage('Cloning Git') {
      steps {
        git 'https://github.com/abhijeet-banerjee/Sample.git'
      }
    }
    stage('Building image') {
      steps{
        script {
        sh "mvn clean package"
        sh "mvn compile"
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          sh "mvn package"
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
  
  
    post
  {
    cleanup
    {
      dir("${workspace}@tmp")
      {
        deleteDir();
      }
       dir("${workspace}@script")
      {
        deleteDir();
      }
    }
  }
}
