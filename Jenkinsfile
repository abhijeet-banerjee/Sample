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
  withMaven(maven: 'mvn') {
            sh "mvn clean package"
        }
}
}

stage('Test')
{
steps
{
  withMaven(maven: 'mvn') {
            sh "mvn compile"
        }
}
}

stage('Deploy')
{
steps
{
  withMaven(maven: 'mvn') {
            sh "mvn package"
        }
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
