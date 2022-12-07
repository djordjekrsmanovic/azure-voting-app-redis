pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Find all fodlers from given folder') {
      steps {
        script {
                    
          def foldersList = []
                    
          def osName = isUnix() ? "UNIX" : "WINDOWS"
          echo "osName: " + osName
    
          echo ".... JENKINS_HOME: ${JENKINS_HOME}"
          echo ".... WORKSPACE:${WORKSPACE}"
    
          if(isUnix()) {
            def output = sh returnStdout: true, script: "ls -l ${JENKINS_HOME} | grep ^d | awk '{print \$9}'"
            foldersList = output.tokenize('\n').collect() { it }
          } else {
            def output = bat returnStdout: true, script: "dir . /b /A:D"
            foldersList = output.tokenize('\n').collect() { it }
                     
          }
          echo ".... " + foldersList
        }            
      }
    }
    stage("Test") {
        sh script:'''
          #!/bin/bash
          echo "This is start $(pwd)"
          mkdir hello
          cd ./hello
          echo "This is $(pwd)"
        '''
    }   
}
