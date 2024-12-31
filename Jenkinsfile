pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: 'refs/heads/main']], // Replace 'main' with your branch name
                    userRemoteConfigs: [[url: 'https://github.com/user/repo.git']]
                ])
            }
        }
    }
}
