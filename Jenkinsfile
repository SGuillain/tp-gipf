pipelin {
  agent{
    agent any
  }
  stages {
        stage('compile') {
            steps { 
              sh './gradlew -Dhttps.proxyHost=proxy1-rech -Dhttps.proxyPort=3128 compile Java'
            }
        }
}
