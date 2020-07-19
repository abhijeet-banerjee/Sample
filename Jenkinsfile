pipeline
{
agent any
tools
{
maven 'M3'
}
stages
{
stage('Build')
{
steps
{
sh "mvn clean package"
}
}

stage('Test')
{
steps
{
sh "mvn compile"
}
}

stage('Deploy')
{
steps
{
sh "mvn package"
}
}

}                      // stages end here.
  
 // post operation performed
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
