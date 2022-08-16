pipeline 
{
    agent any
    stages
        {
            stage('continuous download')
            {
                steps
                {
                    script
                    {
                        
                     try
                        {
                            git 'https://github.com/intelliqittrainings/maven.git'
                        }
                     catch(Exception e1)
                        {
                        mail bcc: '', body: 'Jenkins unable to download the code', cc: '', from: '', replyTo: '', subject: 'Download failed', to: 'git.admin@mygit'
                        exit(1)
                        }
                    }    
                }
            }
            
            stage('continuous build')
            {
                steps
                {
                    script
                    {
                        try
                        {
                           sh 'mvn package' 
                        }
                        catch(Exception e2)
                        {
                            mail bcc: '', body: 'Jenkins unable to create an artifacts', cc: '', from: '', replyTo: '', subject: 'Download failed', to: 'developer.admin@mygit'
                            exit(1)
                        }
                    }
                }
            }
            stage('continuous deployment')
            {
                steps
                {
                    script
                    {
                        try
                        {
                           deploy adapters: [tomcat9(credentialsId: '2e6bf8d6-9b91-4075-b423-e966f305338f', path: '', url: 'http://172.31.10.181:8080')], contextPath: 'test app', war: '**/*.war' 
                        }
                        catch(Exception e3)
                        {
                           mail bcc: '', body: 'Jenkins unable to deploy into QA server', cc: '', from: '', replyTo: '', subject: 'Download failed', to: 'middleware@mygit' 
                          exit(1)
                        }
                    }
                }
            }
            stage('continuous testing')
            {
                steps
                {
                    script
                    {
                        try
                        {
                           git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                           sh 'java -jar /root/.jenkins/workspace/declerativepipeline3/testing.jar' 
                        }
                        catch(Exception e4)
                        {
                          mail bcc: '', body: 'Jenkins unable to test the code', cc: '', from: '', replyTo: '', subject: 'Download failed', to: 'testers@mygit'  
                          exit(1)
                        }
                    }
                }
            }
            stage('continuous delivery')
            {
                steps
                {
                    script
                    {
                        try
                        {
                          deploy adapters: [tomcat9(credentialsId: '2e6bf8d6-9b91-4075-b423-e966f305338f', path: '', url: 'http://172.31.9.38:8080')], contextPath: 'prod app', war: '**/*.war'  
                        }
                        catch(Exception e5)
                        {
                           mail bcc: '', body: 'Jenkins unable to deploy into production', cc: '', from: '', replyTo: '', subject: 'Download failed', to: 'production@mygit' 
                        }
                    }
                 
                }
            }
       }
      }

