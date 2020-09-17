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

  }
}