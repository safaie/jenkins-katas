pipeline {
  agent any
  stages {
    stage('clone down'){
      agent { label 'swarm' }
      steps {
          stash excludes: '.git', name: 'code'
      }
    stage('Say Hello') {
      parallel {
        stage('Say Hello') {
          agent any
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
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
            echo "before workspace deletion"
            sh 'ls -alFh'
            deleteDir()
            echo "after workspace deletion"
            sh 'ls -alFh'
          }
        }

      }
    }

  }
}
