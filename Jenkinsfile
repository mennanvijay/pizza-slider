pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/mennanvijay/pizza-slider.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                dir('vite-project') {
                    // Using full path if needed, or just npm if global install worked
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo rm -rf /var/www/html/*'
                sh 'sudo cp -R vite-project/dist/* /var/www/html/'
            }
        }
    }
}
