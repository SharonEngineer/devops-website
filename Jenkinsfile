pipeline {
    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/SharonEngineer/devops-website.git'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t devops-website:v1 .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f website || true

                docker run -d \
                --name website \
                -p 8081:80 \
                devops-website:v1
                '''
            }
        }
    }
}
