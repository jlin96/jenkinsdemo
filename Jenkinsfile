pipeline {
    agent any

    stages{
        stage('Build Frontend'){
            steps{
                sh "echo Building Frontend"
                sh "cd frontend && npm install && npm run build"
            }
        }

        stage('Deploy Frontend'){
            steps{
                withAWS(region: 'us-east-1', credentials: 'AWS_CREDENTIALS') {
                    sh "aws s3 sync frontend/dist s3://team-6-frontend" 
                }
            }
        }
    }
}