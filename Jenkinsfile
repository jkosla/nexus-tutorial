
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Branch name: ${env.gitlabSourceBranch}"
            }
        }
        stage('Upload Artifacts to Nexus'){
            steps{
                script {
                    def version = "1.0.${env.BUILD_NUMBER}"
                    echo "Using version: ${version}"
                    nexusArtifactUploader artifacts: [[artifactId: 'requirements_artifact_id', 
                        classifier: '', file: 'src/requirements.txt', type: 'txt']], 
                        credentialsId: 'Nexus-Credentials', groupId: 'com.python.tutorial', 
                        nexusUrl: 'http://20.160.102.102:8081', nexusVersion: 'nexus3', 
                        protocol: 'http', repository: 'tutorial', version: version
                }
            }
        }
    }
    post {
        success {
            setGitHubCommitStatus(state: 'SUCCESS', context: 'Pipeline')
        }
        failure {
            setGitHubCommitStatus(state: 'FAILURE', context: 'Pipeline')
        }
        always {
            echo 'Pipeline completed.'
            cleanWs()
        }
    }
}
