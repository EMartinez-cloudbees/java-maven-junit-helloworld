pipeline {
  agent any
  tools { 
    maven 'Maven 3.6.3' 
    jdk 'jdk8' 
  }  
  options { buildDiscarder(logRotator(numToKeepStr: '1')) }

  stages {

    stage('HelloStage') {
      steps {
        sh 'echo "stage Hello $(date)"'
      }
    }
    
    
  }
}
