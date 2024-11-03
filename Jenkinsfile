pipeline {
    angent any
    tools{
        maven 'local_maven'
    }
    stages {
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
               deploy adapters: [tomcat10(credentialsId: 'tomcat_id', path: '', url: 'http://54.242.233.60:9060/')], contextPath: null, war: '**/*.war'
           }
           
       }
    }
}
