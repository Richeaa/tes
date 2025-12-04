pipeline {
    agent any
    
    tools {
        nodejs 'NodeJS-21'  // Sesuaikan dengan nama NodeJS di Jenkins
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
                sh 'npm install'  // 'bat' untuk Windows, 'sh' untuk Linux
            }
        }
        
        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                sh 'npm test'
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
                    echo Deployment successful!
                    echo Application: ${APP_NAME}
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