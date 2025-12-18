
pipeline {
        agent any
        stages {
            stage('compile'){
          steps {
                script { 
                    sh './gradlew -Dhttps.proxyHost=proxy1-rech -Dhttps.proxyPort=3128 compileJava '
                }
            }
        }
          stage('SonarQube Analysis') {
                  steps{
            withSonarQubeEnv() {
              sh "./gradlew sonar"
            }
        }
        }
      }
}
