pipeline {
    agent any
    
    environment {
        // Define your environment variables if needed
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                echo 'Code checkout.'
                git branch: 'springboot-project', url: 'https://github.com/SereyvicheaSaro/Jenkins'
            }
        }
        stage('Build App') {
            steps {
                script {
                    def pom = readMavenPom file: 'pom.xml'
                    version = pom.version
                }
                sh "mvn clean package"
            }
        }
        stage('Testing App') {
            steps {
                echo 'Testing.....'
                sh "mvn test"
            }
        }
    }
    
    post {
        success {
            emailext (
                subject: "Build Success",
                body: "The build of your project was successful.",
                to: "serey.vichea9999@gmail.com"
            )
        }
        failure {
            emailext (
                subject: "Build Failure",
                body: "The build of your project failed.",
                to: "your.email@example.com"
            )
        }
    }
}
