pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS-21'
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
        
        stage('Check Node Version') {
            steps {
                echo '🔍 Checking versions...'
                sh 'node --version'
                sh 'npm --version'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo '📦 Installing dependencies...'
                sh 'npm install'
                sh 'chmod -R +x node_modules/.bin'  // Fix permission untuk semua executables
            }
        }
        
        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                sh 'npm test'  // Sekarang pakai npm test biasa
            }
        }
        
        stage('Build') {
            steps {
                echo '🔨 Building application...'
                sh 'npm run build'
            }
        }
        
        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'
                sh '''
                    echo "Deployment successful!"
                    echo "Application: ${APP_NAME}"
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