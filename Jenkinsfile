
pipeline
    {
       agent any
       environment {
        BOT_TOKEN = '6812251935:AAFxjvNYIPzEn3G6JXfvkqy_C4hQi9T36gQ'
        CHAT_ID = '782285470'
       }
        stages
        {
          stage('Git Checkout') {
            steps {
                echo 'Code checkout.'
                git branch: 'springboot-project', url: 'https://github.com/sereyvicheaSaro/Jenkins'
            }
          }
          stage('Build App')
          {
            steps
             {
              script {
                  def pom = readMavenPom file: 'pom.xml'
                  version = pom.version
              }
              sh "mvn clean package"
            }
          }
          stage('Testing App')
          {
            steps
             {
            echo 'testing.....'
              sh "mvn test"
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