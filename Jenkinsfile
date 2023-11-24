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
      NEXUSIP='44.203.64.106'
      NEXUSPORT='8081'
      NEXUS_LOGIN = 'nexus'  
   }

   stages{
      stage('build') {
         steps {
            sh 'mvn -s settings.xml clean package'
         }
         post {
            success {
               echo 'build success'
               archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
            failure {
               echo 'build failed'
            }
         }
      }
         stage('test') {
            steps {
               sh 'mvn  test'
            }
         }
        stage('checkstyle analys')
        {
          steps
          {
            sh 'mvn checkstyle:checkstyle'
          }
        }

      }
   }






















