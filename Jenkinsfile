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
        stage('Sign Existing Image') {
          steps {
            script {
              def privateKey = Credentials.stringCredentialsByName(
              id: 'cosign_private_key',
              )
              sh "echo '${privateKey.getSecret()}'> cosign.key"
            }
            def imageName = 'sriswetha06/sample-cosign:v2'
              
            sh "cosign sign --key cosign.key $imageName"
          }
    }
}
}
