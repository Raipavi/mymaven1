pipeline
{
    agent any
    stages
    {
        stage('ContDown')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDevlope')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '6225d5e2-40b7-49b5-8dca-70d34a044919', path: '', url: 'http://172.31.25.184:8080')], contextPath: 'jenapp', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '6225d5e2-40b7-49b5-8dca-70d34a044919', path: '', url: 'http://172.31.16.90:8080')], contextPath: 'jenapp', war: '**/*.war'
            }
        }
    }
}
