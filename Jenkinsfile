pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Jenkins automatically pulls code when using 'Pipeline from SCM'
                // But we print a message to confirm
                echo 'Checking out code from GitHub...'
            }
        }

        stage('Verify Files') {
            steps {
                // List files to ensure index.html is there
                sh 'ls -al'
            }
        }

        stage('Publish Pizza Slider') {
            steps {
                // This uses the HTML Publisher plugin we discussed
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: '.',
                    reportFiles: 'index.html',
                    reportName: 'Pizza Slider UI'
                ])
            }
        }
    }
}
