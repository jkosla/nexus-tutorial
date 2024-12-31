pipeline {
    agent any
        stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Branch name: ${env.gitlabSourceBranch}"
            }
        }

        }
}
