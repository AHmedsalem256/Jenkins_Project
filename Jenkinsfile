pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/AHmedsalem256/Jenkins_Test_Github.git'
            }
        }

        stage('Test') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    bat 'robot -d results tests/'
                }
            }
        }

        stage('Report') {
            steps {
                publishHTML (target: [
                    reportDir: 'results',
                    reportFiles: 'report.html',
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    allowMissing: false,
                    reportName: 'Robot Test Report'
                ])
            }
        }
    }

    post {
        always {
            echo "Build finished. Check test results in the 'Robot Test Report'."
        }
    }
}
