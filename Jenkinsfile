pipeline 
{
    agent any
    tools
    {
        jdk 'jdk11'
        maven 'maven3'
    }
    environment
    {
        PRAGARA_STUDENT='Adithya Sivan'
    }
    options
    {
        buildDiscarder(logRotator(numToKeepStr: '3'))
    }
    parameters
    {
        choice(name: 'DEPLOY-ENV', choices: ['UAT1', 'UAT2', 'UAT3'], description: 'SELECT THE ENV')
    }   
    stages
     {
        stage('compile')
         {
            steps
            {
                sh 'mvn compile'
            }
          }
        stage('test')
        {
            steps
            {
                sh 'mvn test'
            }
        }
        stage('package')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Archive Artifact')
        {
            steps
            {
                archiveArtifacts artifacts: 'target/*jar', followSymlinks: false
            }
        }
    } 
}