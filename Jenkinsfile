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
                sh '''
                npm test
                '''
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
            when{
                branch 'main'
            }
            agent{
                docker{
                    image node:18-alpine
                    reuseNode True
                }
            }
            steps {
                sh'''
                npm install netlify-cli
                echo "deploying to netlify'
                netlify deploy --dir=build --prod
                '''
            }
        }
    }
}
