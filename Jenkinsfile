@Library("mylibrary")_
pipeline
{
    agent any
    stages
    {
        stage("continuous downloads_loans")
        {
            steps
            {
              script
              {
                cicd.newgit("https://github.com/intelliqittrainings/maven.git")
              }
                  
             }
        }
        stage('continuous build_loans')
        {
            steps
            {
                script
                {
                  cicd.newbuild()  
                }
            }
        }
        stage('continuous deployment_loans')
        {
            steps
            {
                script
                {
                 cicd.newdeploy("http://172.31.10.181:8080","testapp")   
                }
            }
        }
       }
      } 
