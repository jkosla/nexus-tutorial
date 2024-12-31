
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Branch name: ${env.gitlabSourceBranch}"
            }
        }
        stage('Upload Artifacts to Nexus') {
    stage('Upload Artifacts to Nexus') {
        steps {
            script {
                def version = "1.0.${env.BUILD_NUMBER}"
                echo "Using version: ${version}"
                withCredentials([usernamePassword(credentialsId: 'Nexus-Credentials', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASS')]) {
                    sh """
                    curl -v -u $NEXUS_USER:$NEXUS_PASS \
                        --upload-file src/requirements.txt \
                        http://20.160.102.102:8081/repository/tutorial/com/python/tutorial/requirements_artifact_id/${version}/requirements_artifact_id-${version}.txt
                    """
                }
            }
        }
}

}

//     post {
//     success {
//         githubNotify(context: 'Pipeline', status: 'SUCCESS', description: 'Build succeeded')
//     }
//     failure {
//         githubNotify(context: 'Pipeline', status: 'FAILURE', description: 'Build failed')
//     }
//     always {
//         echo 'Pipeline completed.'
//         cleanWs()
//     }
// }

}
