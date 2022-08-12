pipeline 
{
    agent any
    stages
        {
            stage('continuous download')
            {
                steps
                {
                 git 'https://github.com/intelliqittrainings/maven.git'
                }
            }
            
            stage('continuous build')
            {
                steps
                {
                 sh 'mvn package'
                }
            }
            stage('continuous deployment')
            {
                steps
                {
                 deploy adapters: [tomcat9(credentialsId: '2e6bf8d6-9b91-4075-b423-e966f305338f', path: '', url: 'http://172.31.10.181:8080')], contextPath: 'test app', war: '**/*.war'
                }
            }
            stage('continuous testing')
            {
                steps
                {
                 git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                 sh 'java -jar /root/.jenkins/workspace/declerativepipeline1/testing.jar'
                }
            }
            stage('continuous delivery')
            {
                steps
                {
                 deploy adapters: [tomcat9(credentialsId: '2e6bf8d6-9b91-4075-b423-e966f305338f', path: '', url: 'http://172.31.9.38:8080')], contextPath: 'prod app', war: '**/*.war'
                }
            }
       }
      }
