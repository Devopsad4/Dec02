pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                 git 'https://github.com/Devopsad4/Dec02.git'
            }
        }
        stage('ContinuiusBUild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeploy')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/spt/webapp/target/webapp.war ubuntu@172.31.80.197:/var/lib/tomcat9/webapps/testapp.war'
            }
        }
        stage('COntinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/spt/testing.jar'
            }
        }
        stage('COntinuousDelivery')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/spt/webapp/target/webapp.war ubuntu@172.31.84.117:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
        
    }    
    
}

