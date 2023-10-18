pipeline{
    agent any
    tools {maven "maven"}
    stages {
        stage('clone git') {
          steps{
            git branch: 'main', url: 'https://github.com/nagadurga8/spring-petclinic.git'
          }
        }
          stage('Build') {
              steps {
                  sh 'mvn clean package'
                  
              }
          }
    }
}
