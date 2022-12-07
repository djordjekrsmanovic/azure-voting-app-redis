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
    
    }
      stage('Docker Build') {
         steps {
            // script{
            //   def foldersList = []
            //   bat script: "cd ./azure-vote"
            //   def output2 = bat returnStdout: true, script: "dir . /b /A:D"
            //   foldersList = output2.tokenize('\n').collect() { it }
            //   echo "..." + foldersList
            // }
            steps{
              sh script:'''
          #!/bin/bash
          echo "This is start $(pwd)"
          mkdir hello
          cd ./hello
          echo "This is $(pwd)"
        '''
            }
            // pwsh(script: 'cd azure-vote/')
            
            // pwsh(script: """
            //    cd azure-vote/
            //    docker images -a
            //    docker build -t jenkins-pipeline .
            //    docker images -a
            //    cd ..
            // """)
         }
      }
      // stage('Start test app') {
      //    steps {
      //       pwsh(script: """
      //          docker-compose up -d
      //          ./scripts/test_container.ps1
      //       """)
      //    }
      //    post {
      //       success {
      //          echo "App started successfully :)"
      //       }
      //       failure {
      //          echo "App failed to start :("
      //       }
      //    }
      // }
      // stage('Run Tests') {
      //    steps {
      //       pwsh(script: """
      //          pytest ./tests/test_sample.py
      //       """)
      //    }
      // }
      // stage('Stop test app') {
      //    steps {
      //       pwsh(script: """
      //          docker-compose down
      //       """)
      //    }
      // }
      // stage('Container Scanning') {
      //    parallel {
      //       stage('Run Anchore') {
      //          steps {
      //             pwsh(script: """
      //                Write-Output "blackdentech/jenkins-course" > anchore_images
      //             """)
      //             anchore bailOnFail: false, bailOnPluginFail: false, name: 'anchore_images'
      //          }
      //       }
      //       stage('Run Trivy') {
      //          steps {
      //             sleep(time: 30, unit: 'SECONDS')
      //             // pwsh(script: """
      //             // C:\\Windows\\System32\\wsl.exe -- sudo trivy blackdentech/jenkins-course
      //             // """)
      //          }
      //       }
      //    }
      // }
      // stage('Deploy to QA') {
      //    environment {
      //       ENVIRONMENT = 'qa'
      //    }
      //    steps {
      //       echo "Deploying to ${ENVIRONMENT}"
      //       acsDeploy(
      //          azureCredentialsId: "jenkins_demo",
      //          configFilePaths: "**/*.yaml",
      //          containerService: "${ENVIRONMENT}-demo-cluster | AKS",
      //          resourceGroupName: "${ENVIRONMENT}-demo",
      //          sshCredentialsId: ""
      //       )
      //    }
      // }
      // stage('Approve PROD Deploy') {
      //    when {
      //       branch 'master'
      //    }
      //    options {
      //       timeout(time: 1, unit: 'HOURS') 
      //    }
      //    steps {
      //       input message: "Deploy?"
      //    }
      //    post {
      //       success {
      //          echo "Production Deploy Approved"
      //       }
      //       aborted {
      //          echo "Production Deploy Denied"
      //       }
      //    }
      // }
      // stage('Deploy to PROD') {
      //    when {
      //       branch 'master'
      //    }
      //    environment {
      //       ENVIRONMENT = 'prod'
      //    }
      //    steps {
      //       echo "Deploying to ${ENVIRONMENT}"
      //       acsDeploy(
      //          azureCredentialsId: "jenkins_demo",
      //          configFilePaths: "**/*.yaml",
      //          containerService: "${ENVIRONMENT}-demo-cluster | AKS",
      //          resourceGroupName: "${ENVIRONMENT}-demo",
      //          sshCredentialsId: ""
      //       )
      //    }
      // }
   }
}