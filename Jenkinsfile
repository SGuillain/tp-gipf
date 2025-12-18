pipeline {

    agent any

    triggers {
        cron('H */8 * * *') //regular builds
        pollSCM('* * * * *') //polling for changes, here once a minute
    }

    stages{
      stage('agent any'){
          steps {
                script { 
                    sh './gradlew -Dhttps.proxyHost=proxy1-rech -Dhttps.proxyPort=3128 compileJava '
                }
            }
        }
    }


    node {
      stage('SCM') {
        checkout scm
      }
      stage('SonarQube Analysis') {
        withSonarQubeEnv() {
          sh "./gradlew sonar"
        }
      }
    }
}
