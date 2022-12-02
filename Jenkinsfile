 node('built-in')
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/Devopsad4/Dec02.git'
    }
    stage('COntinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuosDeploy')
    {
        deploy adapters: [tomcat9(credentialsId: '4e6845e2-1324-4996-b81f-3ed0f969f95e', path: '', url: 'http://172.31.80.197:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/spt/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        input message: 'Need aprroval form the DM', submitter: 'Sri swami samarth'
        deploy adapters: [tomcat9(credentialsId: '4e6845e2-1324-4996-b81f-3ed0f969f95e', path: '', url: 'http://172.31.84.117:8080')], contextPath: 'prodapp', war: '**/*.war'
    }

    
    
    
    
}


