pipeline {
  environment {
     registry = "rajidocker2021/project"
     registryCredential = 'dockerhub_ID'
     dockerImage = ''
     //BUILD_NUMBER = 'Latest'
  }
  agent any
  stages {
    
     stage('Build Image') {
         steps {
            echo 'Building Docker Image'
            script {
            //    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                  dockerImage = docker.build registry
            }
         }
    }
      stage('Deploy Image'){
         steps {
            echo 'Pushing Docker Image'
            script {
               docker.withRegistry( '', registryCredential ) {
//               dokcerImage.push("$BUILD_NUMBER")
               dockerImage.push('latest')
              }
            }
          }
       }
       stage('Clean Up'){
           steps {
//               sh "docker rmi $registry:$BUILD_NUMBER"
               sh "docker rmi $registry:latest"
            }
       }
       stage('Deploy'){
            steps {
               echo 'Deploying...'
               sh "/usr/local/bin/kubectl apply -f deployment.yaml"
               sh "/usr/local/bin/kubectl apply -f service.yaml"
               sh "/usr/local/bin/kubectl rollout restart deployment.apps/calc-deployment"
             }
          }
        }

}
       
     
