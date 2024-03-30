
pipeline {
    agent any

    environment {
        BOT_TOKEN = '6812251935:AAFxjvNYIPzEn3G6JXfvkqy_C4hQi9T36gQ'
        CHAT_ID = '782285470'
    }

    stages {
        stage('Git Checkout') {
            steps {
                echo 'Code checkout.'
                git branch: 'midterm', url: 'https://github.com/SereyvicheaSaro/Jenkins/'
            }
        }
        stage('Build App') {
            steps {
                echo 'Building...'
                sh "gradle clean build"
            }
        }
        stage('Testing App') {
            steps {
                echo 'Testing...'
                sh "gradle test"
            }
        }
    }

    post {
        success {
            sh '''
                bash scripts/deployment.sh SUCCESS🟢
            '''
        }
        failure {
            sh '''
                bash scripts/deployment.sh FAILED🔴
            '''
        }
    }
}