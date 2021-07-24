pipeline {
  environment {
     registry = "rajidocker2021/project"
     registryCredential = 'docker-hub'
     dockerImage = ''
  }
  agent any
  stages {
    
     stage('Build Image') {
         steps {
            echo 'Building Docker Image'
            script {
                sockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
         }
    }
      stage('Deploy Image'){
         steps {
            echo 'Pushing Docker Image'
            script {
               docker.withRegistry( '', registryCredential ) {
               dokcerImage.push("$BUILD_NUMBER")
               dockerImage.push('latest')
              }
            }
          }
       }
       stage('Clean Up'){
           steps {
               sh "docker rmi $registry:$BUILD_NUMBER"
               sh "docker rmi $registry:latest"
            }
       }
       stage('Deploy'){
            steps {
               echo 'Deploying...'
               sh "kubectl apply -f deployment.yaml"
               sh "kubectl apply -f service.yaml"
               sh "kubectl rollout reestart deployment.apps/calc-deployment"
             }
          }
        }

}
       
     
