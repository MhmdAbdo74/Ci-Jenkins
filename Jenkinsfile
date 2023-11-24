pipeline {
   agent any 
   tools 
   {
     maven "maven"
     jdk "jdk"
   }
   environment {
      SNAP_REPO = 'vprofile-snapshot'
      NEXUS_USER = 'admin'
      NEXUS_PASSWORD = '12'
      RELEASE_REPO = 'vprofile-release'
      NEXUSIP='172.31.89.205'
      NEXUSPORT='8081'
      NEXUS_LOGIN = 'nexus'  
   }

   stages {
      stage('git checkout') {') { 
         steps {
            sh 'mvn clean package'
         }
      }
      stage('Test') { 
         steps {
            sh 'mvn test'
         }
      }
      stage('Deploy') { 
         steps {
            sh 'mvn deploy'
         }
      }
   }     

}