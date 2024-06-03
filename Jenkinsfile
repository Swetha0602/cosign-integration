pipeline {
    agent any
    stages {
         stage('Install and Verify Cosign') {
            steps {
                script {
                    sh 'cosign version'
                }
            }
        }
    }
}
