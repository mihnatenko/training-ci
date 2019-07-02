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
    stage('Git checkout') {
      steps {
        git(url: 'https://github.com/mihnatenko/training-ci', branch: 'master', credentialsId: 'a89bd138-4e55-4f7c-83ca-14f4604fd57c')
      }
    }
  }
}