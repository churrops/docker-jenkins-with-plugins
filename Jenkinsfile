pipeline {
  agent any
  stages {
    stage('List') {
      steps {
        sh 'ls -lhtr'
        sh '''cd build
docker build -t churrops/jenkins:pipeline .'''
      }
    }
  }
}