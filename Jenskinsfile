pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS-25'  // Sesuaikan dengan nama NodeJS di Jenkins
    }
    
    environment {
        APP_NAME = 'my-nodejs-app'
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo '📥 Pulling code from GitHub...'
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo '📦 Installing dependencies...'
                bat 'npm install'  // 'bat' untuk Windows, 'sh' untuk Linux
            }
        }
        
        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                bat 'npm test'
            }
        }
        
        stage('Build') {
            steps {
                echo '🔨 Building application...'
                bat 'npm run build'
            }
        }
        
        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'
                bat '''
                    echo Deployment successful!
                    echo Application: %APP_NAME%
                '''
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline succeeded!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
        always {
            echo '🧹 Cleaning up workspace...'
        }
    }
}