pipeline {
  agent any
  stages {
    stage('Clone Source') {
      parallel {
        stage('Git Checks') {
          steps {
            git(url: 'https://github.com/fmaulana240699/docker-pipeline.git', branch: 'master', poll: true)
          }
        }

        stage('Cloning Source') {
          steps {
            sh 'rm -rf *'
            sh 'git clone https://github.com/fmaulana240699/docker-pipeline.git'
          }
        }

        stage('Verify Clone') {
          steps {
            sh 'ls -l'
          }
        }

      }
    }

    stage('Build Images') {
      parallel {
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

        stage('verify images') {
          steps {
            sh 'docker images'
          }
        }

      }
    }

    stage('Deploy Images') {
      steps {
        sh 'docker run -tid -p 80:80 fmaulana24/testing-pipeline:v1'
      }
    }

  }
}