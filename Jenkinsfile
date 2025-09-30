pipeline {
    agent any
    stages {
        stage('Build Backend') {
            steps {
                dir('backend') {
                    sh 'npm install'
                    sh 'npm run build'   // if your backend needs a build step
                }
            }
        }
        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    sh 'npm install'
                    sh 'npm run build'   // frontend build, usually creates a build/ folder
                }
            }
        }
        stage('Deploy') {
            steps {
                // Example: copy frontend build files
                sh 'scp -r frontend/build/* user@server123:/var/www/mywebsite/'
                
                // Optional: deploy backend
                sh 'scp -r backend/* user@server123:/var/www/mywebsite-backend/'
                
                // You may need to restart backend server if using Node.js
                sh 'ssh user@server123 "pm2 restart backend-app || pm2 start backend/app.js --name backend-app"'
            }
        }
    }
}
