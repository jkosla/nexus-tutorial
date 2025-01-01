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
            steps {
                script {
                    echo "Using version: ${BUILD_NUMBER}"
                    withCredentials([usernamePassword(credentialsId: 'Nexus-Credentials', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASS')]) {
                        sh '''
                        curl -v -u $NEXUS_USER:$NEXUS_PASS \
                            --upload-file src/require.txt \
                            http://20.160.102.102:8081/repository/tutorial/com/python/tutorial/requirements_artifact_id/${BUILD_NUMBER}/requirements_artifact_id-$BUILD_NUMBER.txt
                        '''
                    }
                }
            }
        }
    }
}
