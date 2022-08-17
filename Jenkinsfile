@Library("mylibrary")_
pipeline
{
    agent any
    stages
    {
        stage("continuous downloads_master")
        {
            steps
            {
              script
              {
                cicd.newgit("https://github.com/intelliqittrainings/maven.git")
              }
                  
             }
        }
        stage('continuous build_master')
        {
            steps
            {
                script
                {
                  cicd.newbuild()  
                }
            }
        }
        stage('continuous deployment_master')
        {
            steps
            {
                script
                {
                 cicd.newdeploy("http://172.31.10.181:8080","testapp")   
                }
            }
        }
        stage('continuous testing_master')
        {
            steps
            {
                script
                {
                    cicd.newgit("https://github.com/intelliqittrainings/FunctionalTesting.git")
                    cicd.newtest("phaneendra")
                }
            }
        }
        stage('continuous delivery_master')
        {
            steps
            {
                script
                {
                 cicd.newdeploy("http://172.31.9.38:8080","prodapp")   
                }
            }
        }
    }
}
