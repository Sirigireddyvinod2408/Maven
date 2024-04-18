pipeline
{
    agent any
    stages
    {
        stage('Cont Download')
        {
            steps
            {
               git 'https://github.com/Sirigireddyvinod2408/maven.git' 
            }
        }
        stage('Cont Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Cont Deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '06683349-5840-401c-a23e-9e177563e128', path: '', url: 'http://172.31.28.201:8080')], contextPath: 'testapplication', war: '**/*.war'
            }
        }
        stage('Cont Test')
        {
            steps
            {
                git 'https://github.com/Sirigireddyvinod2408/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline_PollSCM/testing.jar'
            }
        }
        stage('Cont Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '06683349-5840-401c-a23e-9e177563e128', path: '', url: 'http://172.31.19.67:8080')], contextPath: 'productionapplication', war: '**/*.war'
            }
        }
    }
}
