pipeline {
    agent any // Run on any available agent

    stages {
        // Stage 1: Print "Hello, Jenkins!"
        stage('Say Hello') {
            steps {
                echo 'Hello, Jenkins!'
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