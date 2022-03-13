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

    stage('Creating container with project image to deploy'){
       steps {
          echo 'Deploy project image through container'

          sh 'docker run -dt --name chinna_proj_cont mainproject_chinna'
}

}

       
}    
} 
