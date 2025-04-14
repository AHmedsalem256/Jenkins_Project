pipeline {
    agent any

    environment {
        ROBOT_REPORT_DIR = 'robot-reports'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/AHmedsalem256/Jenkins_Project.git'
            }
        }

        stage('Run Robot Framework Tests') {
            steps {
                bat "robot --outputdir %ROBOT_REPORT_DIR% tests/"
            }
        }

        stage('Publish Robot Report') {
            steps {
                publishHTML([
                    reportDir: 'robot-reports',
                    reportFiles: 'report.html',
                    reportName: 'Robot Test Report',
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true
                ])
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'robot-reports/*.html', allowEmptyArchive: true
        }
    }
}
