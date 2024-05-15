pipeline {
    agent any

    stages {
        stage('Git Reprosatory') {
            steps {
                git branch: 'main', url: 'https://github.com/chowdhruy/jk-public.git'
            }
        }
          stage('Docker Images') {
            steps {
              sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Deploy Project') {
            steps {
                sh '''
                #docker stop webapp_ctr
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
                '''
            }
        }
    }
}
