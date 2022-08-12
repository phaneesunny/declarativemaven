pipeline
{
    agent any
    stages
    {
        stage('continuousDownloads')
        {
            steps
            {
                git 'https://github.com/phaneesunny/declarativemaven.git'
            }
        }
        stage('continuousBuild')
        {
            steps
            {
               sh 'mvn package' 
            }
        }
        stage('continuousDeployment')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'aa911521-13ff-49b0-8d1a-25520692cc5d', path: '', url: 'http://172.31.10.181:8080')], contextPath: 'qaserver', war: '**/*.war' 
            }
        }
        stage('continuousTesting')
        {
            steps
            {
              git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
              sh 'java  -jar /home/ubuntu/.jenkins/workspace/declerativepipeline1/testing.jar'
            }
        }
        stage('continuousDelivery')
        {
            steps
            {
              deploy adapters: [tomcat9(credentialsId: 'aa911521-13ff-49b0-8d1a-25520692cc5d', path: '', url: 'http://172.31.9.38:8080')], contextPath: 'pdserver', war: '**/*.war'  
            }
        }
    }
}
