pipeline {
  agent any
  stages {
    stage('Clone Source') {
      parallel {
        stage('Verify Cloning Source') {
          steps {
            sh 'ls -l'
          }
        }

        stage('Cloning CODE') {
          steps {
            git(url: 'https://github.com/fmaulana240699/docker-pipeline.git', branch: 'master')
          }
        }

      }
    }

    stage('Build Images') {
      parallel {
        stage('Verify Images') {
          steps {
            sh 'docker images'
          }
        }

        stage('Tag Images') {
          steps {
            sh 'docker tag testing-pipeline fmaulana24/testing-pipeline:v1'
          }
        }

        stage('Build Images') {
          steps {
            sh 'docker build -t testing-pipeline . '
          }
        }

      }
    }

    stage('Check Images') {
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