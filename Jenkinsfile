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
                // Assuming test cases are in a .robot file like "tests/my_tests.robot"
                bat 'robot -d results tests/'
            }
        }

        stage('Report') {
            steps {
                // Publish the Robot Framework report
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
}
