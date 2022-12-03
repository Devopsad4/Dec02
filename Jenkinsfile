
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

=======
        stage('COntinuousDownload')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/Devopsad4/Dec02.git'
                    }
                    catch(Exception e1)
                    {
                        mail bcc: '', body: 'Jenkins has failed to download the code form git hub', cc: '', from: '', replyTo: '', subject: 'Download Failded in ', to: 'gitadmim'
                        exit(1)
                    }
                }
            }
        }
        stage('ContinuousBuild')
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
                        mail bcc: '', body: 'Jenkins is unable to create artifact form downloa code', cc: '', from: '', replyTo: '', subject: 'Build Failded', to: 'dev.team'
                    }
                }
            }
        }
        stage('COntinuousDeploy')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'scp /home/ubuntu/.jenkins/workspace/DeH/webapp/target/webapp.war ubuntu@172.31.80.197:/var/lib/tomcat9/webapps/testapp.war'
                    }
                    catch(Exception e3)
                    {
                        mail bcc: '', body: 'Jenkins is unable to deploy the artifact into the tomcat qa server', cc: '', from: '', replyTo: '', subject: 'Deployment failed', to: 'midddlewar.team'
                        exit(1)
                    }
                }
            }
        }
        
        
        stage('COntiuousTesting')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/Devopsad4/FunctionTesting.git'
                        sh 'java -jar /home/ubuntu/.jenkins/workspace/DeH/testing.jar'
                    }
                    catch(Exception e4)
                    {
                         mail bcc: '', body: 'Selenium script showing failed', cc: '', from: '', replyTo: '', subject: 'Testing Failed', to: 'qa.team'
                         exit(1)
                    }
                }
            }
        }
        
        stage('ContinuousDelivery')
        {
            steps
            {
                script
                {
                    try
                    {
                        input message: 'Need Approval From the DM', submitter: 'Shri Swami Samarth'
                        sh 'scp /home/ubuntu/.jenkins/workspace/DeH/webapp/target/webapp.war ubuntu@172.31.84.117:/var/lib/tomcat9/webapps/prodapp.war'
                    }
                    catch(Exception e5)
                    {
                        mail bcc: '', body: 'Jenkin is unable to deploy into tomcat on the prodserver', cc: '', from: '', replyTo: '', subject: 'Delivery failed', to: 'delivery.team'
                        exit(1)
                    }
                }
            }
        }
        
        
        
        
        
        
        
        
        
        
    }
}
>>>>>>> f2f0853 (jenkiE)
