pipeline {
  agent any
  options { buildDiscarder(logRotator(numToKeepStr: '1')) }
  
  stages {

    stage('HelloStage') {
      steps {
        sh 'echo "stage Hello $(date)"'
      }
    }
    
    
  }
}
