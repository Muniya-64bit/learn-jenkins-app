pipeline {
    agent any // Run on any available agent

    stages {
        // Stage 1: Print "Hello, Jenkins!"
        stage('Build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                ls -la
                npm --version
                npm ci
                npm run build
                '''
            }
        }
    }

    post {
        // Actions to perform after the pipeline completes
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}