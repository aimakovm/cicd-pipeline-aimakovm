pipeline {
  agent any
  stages {
    stage('1') {
      parallel {
        stage('1') {
          steps {
            sleep 3
            echo 'hi'
          }
        }

        stage('') {
          steps {
            echo 'lol'
          }
        }

      }
    }

    stage('2') {
      steps {
        echo 'step 2'
      }
    }

  }
}