pipeline {
  agent any
  stages {
    stage('Clone Source') {
      steps {
        git(url: 'https://github.com/fmaulana240699/docker-pipeline.git', branch: 'master', poll: true)
      }
    }

  }
}