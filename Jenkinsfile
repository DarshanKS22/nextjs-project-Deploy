pipeline {
    agent any
    
        tools {
        nodejs "node18"
    }

    environment {
        // 'vercel_token' must be a Jenkins Secret Text credential
        VERCEL_TOKEN = credentials('vercel_token')
    }

    stages {
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Skipping tests - no test script found'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                // use $VERCEL_TOKEN on Unix-like shells
                sh 'npx vercel --prod --yes --token="$VERCEL_TOKEN"'
            }
        }
    }
}
