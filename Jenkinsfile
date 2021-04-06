pipeline {
  agent any
  stages {
    stage('Say Hello') {
      parallel {
        stage('welcome message') {
          steps {
            sh 'echo "Hello World!"'
          }
        }

        stage('build app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'echo "It should build something here!"
            sh 'ci/build-app.sh'
          }
        }

      }
    }

  }
}
