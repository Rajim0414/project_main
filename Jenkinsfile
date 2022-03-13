pipeline {
   environment {
      registry = "rajidocker2021/mainproject_chinna"
}
  agent any
  stages {
     stage('Checkout devops proj') {
        steps {
            git branch: 'branch_chinna',
                credentialsId: 'my_cred_id',
                url: 'https://github.com/Rajim0414/project_main.git'

            sh "ls -lat"
        }
    } 
    
    stage('Building Docker Project image') {
        steps { 
           echo 'Building docker image'
            
           script {
           dockerImage = docker.build registry
}
}
}

       
}    
} 
