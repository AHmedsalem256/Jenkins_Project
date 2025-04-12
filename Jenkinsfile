pipeline {
    agent any

    environment {
        ROBOT_REPORT_DIR = 'robot-reports'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/AHmedsalem256/Jenkins_Project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt' // if you have one
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
                publishHTML (target : [
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

    post {
        always {
            archiveArtifacts artifacts: 'robot-reports/*.html', allowEmptyArchive: true
        }
    }
}
