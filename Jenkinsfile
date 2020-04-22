pipeline {
  agent any
  
  environment {
    ORIG_AUTHOR = "Elena Martinez"
  }
    
  tools { 
    maven 'M3' 
  }  
  options { buildDiscarder(logRotator(numToKeepStr: '1')) }

  stages {

    stage('HelloStage') {
      environment {
        STAGE_AUTHOR = "HelloStage Elena Martinez"
      }
      steps {
        sh '''
          echo "Hello Junit Maven Pipeline $(date)"
          echo "PATH=${PATH}"
          echo "M2_HOME=${M2_HOME}"
          echo "BUILD_NUMBER=${BUILD_NUMBER}"
          echo "NODE_NAME=${NODE_NAME}"
          echo "JOB_NAME=${JOB_NAME}"
          echo "BRANCH_NAME=${BRANCH_NAME}"
          echo "CHANGE_AUTHOR=${CHANGE_AUTHOR}"          
          echo "CHANGE_AUTHOR_DISPLAY_NAME=${CHANGE_AUTHOR_DISPLAY_NAME}"  
          echo "ORIG_AUTHOR=${ORIG_AUTHOR}"
          echo "STAGE_AUTHOR=${STAGE_AUTHOR}"  
                 
        '''
      }
    }
    
    
    stage('Build') {
      steps {
        sh '''
          echo "Maven build $(date)"
          echo "ORIG_AUTHOR=${ORIG_AUTHOR}"
          echo "STAGE_AUTHOR=${STAGE_AUTHOR}"            
          mvn install
        '''
        withEnv(["STAGE_AUTHOR=BuildStageElenaMartinez"]) {
          echo "STAGE_AUTHOR=${STAGE_AUTHOR}"           
        }
      }
    }
    
    stage('Parallel Stages') {
    
      parallel {
      
        stage('Archive') {
          steps {
            sh '''
              echo "Archive jars: $(date)"
            '''      
            archiveArtifacts(artifacts: 'target/**/*.jar', fingerprint: true) 
          }
        }
    
        stage('Test') {
          steps {
            sh '''
              echo "Publish test results $(date)"
            '''
            junit(testResults: 'target/failsafe-reports/**/*.xml', allowEmptyResults: true)
          }
        }
        
      }
                      
    }
    
    
  }
}
