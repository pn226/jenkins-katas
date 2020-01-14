pipeline {
  agent any
  stages {
    stage('Clone Down') {
      steps {
        stash(excludes: '.git', name: 'code')
      }
    }

    stage('Hello') {
      parallel {
        stage('Hello') {
          steps {
            sh 'echo "hello world"'
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
            archiveArtifacts '*'
          }
        }

      }
    }

  }
}