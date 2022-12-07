pipeline {
    agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }

      stage("Test") {
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
      
   }
}
   
     
