pipeline {
    agent any
    stages {

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
               deploy adapters: [tomcat10(credentialsId: 'tomcat_id', path: '', url: 'http://http://54.226.104.81:9060/')], contextPath: null, war: '**/*.war'
           }
           
       }
    }
}
