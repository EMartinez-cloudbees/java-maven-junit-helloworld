pipeline {
  agent any
  tools { 
    maven 'Maven_3.6.3' 
  }  
  options { buildDiscarder(logRotator(numToKeepStr: '1')) }

  stages {

    stage('HelloStage') {
      steps {
        sh '''
          echo "Hello Junit Maven Pipeline $(date)"
          echo "PATH=${PATH}"
          echo "M2_HOME=${M2_HOME}"
        '''
      }
    }
    
    
    stage('Build') {
      steps {
        sh '''
          echo "Maven build $(date)"
          mvn install
        '''
      }
    }
    
    
  }
}
