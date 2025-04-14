pipeline {
  agent any

  environment {
    ROBOT_REPORT_DIR = 'robot-reports'
  }

  stages {
    stage('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/AHmedsalem256/Jenkins_Project.git'
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

  }

  post {
    always {
      archiveArtifacts(artifacts: 'robot-reports/*.html', allowEmptyArchive: true)
    }
  }
}
