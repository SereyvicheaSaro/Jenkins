
pipeline
    {
       agent any
       environment {
        BOT_TOKEN = '6451695822:AAEvuVexMDi5jgKLycHSe_q45vvSFrsp9b8'
        CHAT_ID = '-1002142392049'
       }
        stages
        {
          stage('Git Checkout') {
            steps {
                echo 'Code checkout.'
                git branch: 'springboot-project', url: 'https://github.com/Mony-Ratanak/DevOps/'
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