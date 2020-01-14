pipeline {
  agent any
  stages {
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
          }
        }

      }
    }

    stage('build app') {
      agent {
        docker {
          image 'gradle:jdk11'
        }

      }
      steps {
        archiveArtifacts 'app/build/libs/'
      }
    }

  }
}