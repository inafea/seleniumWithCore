pipeline {
  agent any
  triggers{
  githubPush()
  }
  stages {
    stage('hello') {
      steps {
        echo 'hello from preprod'
      }
    }

  }
}
