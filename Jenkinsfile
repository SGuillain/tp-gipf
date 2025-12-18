pipeline {

    agent any

    triggers {
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
        stage('SonarQube Analysis') {
            withSonarQubeEnv() {
              sh "./gradlew sonar"
            }
        }
    }
}
