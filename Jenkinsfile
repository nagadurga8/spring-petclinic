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
            git branch: 'main', credentialsId: 'edc43311-5408-4645-8be5-df7162b7f887', url: 'https://github.com/nagadurga8/spring-petclinic.git'
          }
        }
          stage('Build') {
              steps {
                  sh 'mvn clean package'
                  
              }
          }
      stage('Copy Artifact') {
           steps { 
                   sh 'pwd'
		   sh 'cp -r target/*.jar docker'
           }
        }
         
        stage('Build docker image') {
           steps {
               script {         
                 def customImage = docker.build('naga9889/petclinic', "./docker")
                 docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                 customImage.push("${env.BUILD_NUMBER}")
                 }                     
           }
        }
	  }
   }
}
