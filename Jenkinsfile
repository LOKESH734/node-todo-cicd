pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh '''
                  node --version
                  npm --version
                  npm install
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing broo'
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                  docker build -t tiger-app .
                '''
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                  docker rm -f tiger-app || true
                  docker run -d -p 8000:8000 --name tiger-app tiger-app
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying broo'
            }
        }
    }
}
