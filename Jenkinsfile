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
          mkdir hello
          cd ./hello
          echo "This is $(pwd)"
        '''
        }
        
    }
      
   }
}
   
     
