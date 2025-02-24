pipeline {
    agent any // Run on any available agent

    stages {
        // Stage 1: Print "Hello, Jenkins!"
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine' // Use Node.js 18 Alpine image
                    reuseNode true // Reuse the same workspace
                }
            }
            steps {
                sh '''
                echo "Checking Node.js and npm versions..."
                node --version
                npm --version

                echo "Installing dependencies..."
                npm ci

                echo "Building the application..."
                npm run build
                ls -la
                '''
            }
        }

        // Stage 2: Run Tests
        stage('Tests') {
            agent {
                docker {
                    image 'node:18-alpine' // Use Node.js 18 Alpine image
                    reuseNode true // Reuse the same workspace
                }
            }
            steps {
                sh '''
                echo "Running tests..."
                npm test
                ls -la
                '''
            }
        }
    }

    post {
        // Archive test results
        always {
            junit 'test-results/junit.xml' // Archive JUnit test results
        }

        // Actions to perform after the pipeline completes
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}