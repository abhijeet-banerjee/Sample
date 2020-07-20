pipeline {
  
  agent any
  stages {
    
    stage('Building') {
      steps{
sh "mvn clean package"
      }
    }
    
    stage('Test') {
      steps{
sh "mvn compile"
      }
    }
    
    stage('Deploy') {
      steps{
        sh "mvn package"
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
