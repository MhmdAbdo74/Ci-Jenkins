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
      NEXUS_PASS = '12'
      RELEASE_REPO = 'vprofile-release'
      NEXUSIP='172.31.89.205'
      NEXUSPORT='8081'
      CENTRAL_REPO='vpro-maven-central'
      NEXUS_GRP_REPO='vpro-maven-group'
      NEXUS_LOGIN = 'nexus'
      SONARSERVER = 'sonar'
      SONARSCANNER = 'sonar'  
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

      

              stage('Sonar Analysis') {

            steps {
               withSonarQubeEnv("${SONARSERVER}") {
                   sh '''${SONARSCANNER}/bin/sonar-scanner -Dsonar.projectKey=vprofile \
                   -Dsonar.projectName=vprofile \
                   -Dsonar.projectVersion=1.0 \
                   -Dsonar.sources=src/ \
                   -Dsonar.java.binaries=target/test-classes/com/visualpathit/account/controllerTest/ \
                   -Dsonar.junit.reportsPath=target/surefire-reports/ \
                   -Dsonar.jacoco.reportsPath=target/jacoco.exec \
                   -Dsonar.java.checkstyle.reportPaths=target/checkstyle-result.xml'''
              }
            }
        }
   }
   }















