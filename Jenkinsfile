pipeline {
  agent any
  stages {
    stage('Build ') {
      parallel {
        stage('Build ') {
          steps {
            echo 'HEllo Wolrld'
          }
        }

        stage('Build_1') {
          steps {
            echo 'Hello World'
          }
        }

      }
    }

    stage('Test') {
      steps {
        echo 'Test_Done '
      }
    }

    stage('Deploy ') {
      steps {
        echo 'HElllll'
      }
    }

  }
}