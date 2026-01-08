pipeline {
    agent any

    tools {
        // This must match the name you gave in 'Manage Jenkins > Tools'
        nodejs 'LocalNode' 
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/mennanvijay/pizza-slider.git', branch: 'main'
            }
        }

        stage('Install & Build') {
            steps {
                dir('vite-project') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy to Apache') {
            steps {
                // 1. Clear the old files in the web server
                sh 'sudo rm -rf /var/www/html/*'
                
                // 2. Copy the new 'dist' folder content to Apache
                sh 'sudo cp -R vite-project/dist/* /var/www/html/'
                
                echo "Successfully Deployed! Check http://your-ec2-ip/"
            }
        }
    }
}
