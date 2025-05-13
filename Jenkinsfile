pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                sh './gradlew clean test'
            }
        }

        stage('Publish Test Results') {
            steps {
                junit 'build/test-results/test/*.xml'
            }
        }

        stage('Publish HTML Report') {
            steps {
                publishHTML(target: [
                    reportName : 'Unit Test Report',
                    reportDir  : 'build/reports/tests/test',
                    reportFiles: 'index.html',
                    keepAll    : true
                ])
            }
        }
    }
}
