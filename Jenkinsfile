pipeline {
    agent any
    stages {
         stage('Install and Verify Cosign') {
            steps {
                script {
                    sh 'curl -L https://github.com/sigstore/cosign/releases/download/v1.2.2/cosign-v1.2.2-linux-amd64.gz -o cosign.gz'
                    sh 'gunzip cosign.gz'
                    sh 'gunzip cosign.gz'
                    sh 'sudo mv cosign /usr/local/bin/cosign'
                    sh 'sudo chmod +x /usr/local/bin/cosign'
                    sh 'cosign version'
                }
            }
        }
    }
}
