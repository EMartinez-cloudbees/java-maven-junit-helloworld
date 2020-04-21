pipeline {
  agent any
  tools { 
    maven 'Maven_3.6.3' 
  }  
  options { buildDiscarder(logRotator(numToKeepStr: '1')) }

  stages {

    stage('HelloStage') {
      steps {
        sh 'echo "Hello Junit Maven Pipeline $(date)"'
      }
    }
    
    
  }
}
