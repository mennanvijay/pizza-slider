pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulling the code from your repo
                git url: 'https://github.com/mennanvijay/pizza-slider.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                dir('vite-project') {
                    // Running npm commands directly
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Cleaning old files and moving the new build to Apache
                sh 'sudo rm -rf /var/www/html/*'
                sh 'sudo cp -R vite-project/dist/* /var/www/html/'
                echo "Deployment Complete! Visit your EC2 Public IP."
            }
        }
    }
}
