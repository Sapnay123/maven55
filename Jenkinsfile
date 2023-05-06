pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/Sapnay123/maven55.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeploymentt')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/declarativepipeline/testing.jar'

            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'dd6f73b4-9974-4dfc-ab04-ff8daf4008b8', path: '', url: 'http://172.31.23.93:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('CD')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'dd6f73b4-9974-4dfc-ab04-ff8daf4008b8', path: '', url: 'http://172.31.16.199:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
