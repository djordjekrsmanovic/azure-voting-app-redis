pipeline {
    agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

      stage("Docker build") {
        steps{
          bat script:'''
          #!/bin/bash
          echo "This is start $(pwd)"
          cd ./azure-vote
          docker images -a
          docker build -t app-image .
          docker images -a
          echo "This is $(pwd)"
        '''
        } 
      } 

      stage("Start application"){
        steps{
          bat script: ''' 
             docker-compose up
          '''
        }
        post{
          success{
            echo "App started successfully"
          }
          failure{
            echo "App can not start"
          }
        }
      }
      
   }
}
   
     
