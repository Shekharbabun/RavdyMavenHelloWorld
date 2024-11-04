pipeline {
    agent any
    stages {
        stage ('Git checkout') {
           steps{
            https://github.com/Shekharbabun/RavdyMavenHelloWorld.git
                }
        }
    tools{
        maven 'local_maven'
    }
    
       stage ('Build') {
           steps{
               sh 'mvn clean package'
           }
           post {
               success{
                   echo "Archiving the Artifacts"
                   archiveArtifacts artifacts: '**/target/*.war'
               }
           }
           
       }
       
       stage('Deploy to Tomcat server') {
           steps{
               deploy adapters: [tomcat10(credentialsId: 'tomcat_id', path: '', url: 'http://54.236.5.248:9060/')], contextPath: null, war: '**/*.war'
           }
           
       }
    }
}
