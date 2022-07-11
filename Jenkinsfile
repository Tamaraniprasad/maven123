pipeline
{
    agent any
    stages
    {
     stage('ContinuousDownload_loans')    
     {
         steps
         {
             git 'https://github.com/Tamaraniprasad/maven123.git'
         }
     }
     stage('ContinuousBuild_loans')    
     {
         steps
         {
             sh 'mvn package'
         }
     }
    } 
}
