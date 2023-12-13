pipeline {
  environment {
  registry = "snehal01102002/poe"
  registryCredential = 'dock_id'
  dockerImage = ''
}
agent any
stages {
        stage('Build image') 
        {
          steps{
            script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                    }
                }
         }
         stage('Deploy the image') 
         {
            steps{
              script {
                  docker.withRegistry( '', registryCredential ) 
                      {
                        dockerImage.push()
                      }
                  }
                }
          }

  }
}
