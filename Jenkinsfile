pipeline {
  agent any
  stages {
    stage('Cloning CODE') {
      steps {
        sh 'rm -rf *'
        git(url: 'https://github.com/fmaulana240699/docker-pipeline.git', branch: 'master')
        sh 'ls -l'
      }
    }

    stage('Build Images') {
      steps {
        sh 'docker build -t testing-pipeline . '
      }
    }

    stage('Tag Images') {
      steps {
        sh 'docker tag testing-pipeline fmaulana24/testing-pipeline:v1'
      }
    }

    stage('Verify Images') {
      steps {
        sh 'docker images'
      }
    }

    stage('Deploy Images') {
      steps {
        sh 'docker run -tid -p 80:80 fmaulana24/testing-pipeline:v1'
      }
    }

  }
}