pipeline {
  agent {
    node {
      label 'slave'
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
    stage('Run Tests') {
      steps {
        dir(path: 'flask-app') {
          sh '''docker-compose down
docker-compose build flask-app
docker-compose run flask-app pytest -v --junit-xml=/var/opt/junit-report/report.xml
docker-compose down
'''
        }

        junit(testResults: 'flask-app/junit-report/report.xml', allowEmptyResults: true)
        sh 'sudo rm -rf flask-app/junit-report'
      }
    }
  }
}