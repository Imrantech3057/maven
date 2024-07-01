node('built-in') 
{
    stage('continuous download')
    {
        git 'https://github.com/Imrantech3057/maven.git'
    }
    stage('continuous build')
    {
        sh 'mvn package'
    }
    stage('continuous deploy')
    {
        deploy adapters: [tomcat9(credentialsId: 'eb6c38f0-5016-4fed-9063-326a1e64d126', path: '', url: 'http://172.31.22.103:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuous testing')
    {
        git 'https://github.com/Imrantech3057/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('continuous delivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'eb6c38f0-5016-4fed-9063-326a1e64d126', path: '', url: 'http://172.31.27.69:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
