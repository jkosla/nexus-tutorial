pipeline {
    agent any  // Use any available agent

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Add your build commands here, e.g., Maven, Gradle, etc.
                sh 'echo "Build step"'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here, e.g., running unit tests
                sh 'echo "Test step"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add your deployment commands here
                sh 'echo "Deploy step"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
