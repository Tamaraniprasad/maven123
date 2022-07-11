pipeline
{
    agent any
    stages
    {
     stage('ContinuousDownload')    
     {
         steps
         {
             git 'https://github.com/intelliqittrainings/maven.git'
         }
     }
     stage('ContinuousBuild')    
     {
         steps
         {
             sh 'mvn package'
         }
     }     
    stage('ContinuousDeployment')    
     {
         steps
         {
            deploy adapters: [tomcat9(credentialsId: '8c124f2c-c5a0-4a88-8fd3-1dff50e01602', path: '', url: 'http://172.31.11.246:8080')], contextPath: 'siva', war: '**/*.war'
         }
     }
     stage('ContinuousTesting')
     {
         steps
         {
             git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
             sh 'java -jar /var/lib/jenkins/workspace/Declaretivepipeline/testing.jar'
         }
     }
     stage('ContinuousDelivery')
     {
         steps
         {
           deploy adapters: [tomcat9(credentialsId: '8c124f2c-c5a0-4a88-8fd3-1dff50e01602', path: '', url: 'http://172.31.4.143:8080')], contextPath: 'siva', war: '**/*.war'    
            input message: 'Need approval from DM', submitter: 'devi'           
         }
     }
    }
}
