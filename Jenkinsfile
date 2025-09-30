pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                dir('frontend') {  // replace 'frontend' with your folder name
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp -r frontend/build/* user@server123:/var/www/mywebsite/'  // adjust paths
            }
        }
    }
}
