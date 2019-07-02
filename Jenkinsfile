pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Echo text') {
      steps {
        sh 'echo "Hello, Jenkins"'
      }
    }
  }
}