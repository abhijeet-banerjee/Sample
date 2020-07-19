pipeline
{
agent any
tools
{
maven "Maven 3.6.3"
}
stages
{
stage('Build')
{
steps
{
sh "${mvnHome}/bin/mvn clean"
}
}

stage('Test')
{
steps
{
sh "${mvnHome}/bin/mvn compile"
}
}

stage('Deploy')
{
steps
{
sh "${mvnHome}/bin/mvn package"
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
