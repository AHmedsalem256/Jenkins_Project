pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git 'https://github.com/AHmedsalem256/Jenkins_Project.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'pip install -r requirements.txt'
        bat 'pip install robotframework'
        bat 'pip install robotframework-seleniumlibrary'
      }
    }

    stage('Run Robot Tests') {
      steps {
        bat 'robot --outputdir %ROBOT_REPORT_DIR% tests/'
      }
    }

    stage('Publish Robot Report') {
      steps {
        publishHTML([
                              allowMissing: false,
                              alwaysLinkToLastBuild: true,
                              keepAll: true,
                              reportDir: 'robot-reports',
                              reportFiles: 'report.html',
                              reportName: 'Robot Test Report'
                          ])
        }
      }

    }
    environment {
      ROBOT_REPORT_DIR = 'robot-reports'
    }
    post {
      always {
        archiveArtifacts(artifacts: 'robot-reports/*.html', allowEmptyArchive: true)
      }

    }
  }