pipeline{
    agent any
    tools {maven "maven"}
     environment {
      RELEASE_REPO = 'petclinic'
      NEXUS_IP = '54.90.109.24'
      NEXUS_PORT ='8081'
      NEUXS_LOGIN ='neuxs'
      DOCKERHUB_CREDENTIALS = credentials('docker-token')
      REGISTRY = 'petclinic'
     }
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
