
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
                
        stage('Unit & Integration Tests') {
                    steps {
                        script {
                            try {
                                sh './gradlew clean test --no-daemon' //run a gradle task
                            } finally {
                                junit '**/build/test-results/test/*.xml' //make the junit test results available in any case (success & failure)
                            }
                        }
                    }
                }

        stage('jar'){
                  steps {
                        script { 
                            sh './gradlew -Dhttps.proxyHost=proxy1-rech -Dhttps.proxyPort=3128 jar '
                        }
                    }
                }

                post {
                always {
                    archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                    junit 'build/reports/**/*.xml'
                }
            }
          //stage('SonarQube Analysis') {
                  //steps{
            //withSonarQubeEnv() {
              //sh "./gradlew sonar"
            //}
        //}
        //}
      }
}
