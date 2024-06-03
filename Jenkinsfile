pipeline {
    agent any
    environment {
        GITHUB_TOKEN=credentials('Github_creds')
        IMAGE_NAME='sriswetha06/sample-cosign'
        IMAGE_VERSION='v2'
        COSIGN_PASSWORD=credentials('cosign-password')
        COSIGN_PRIVATE_KEY=credentials('cosign-private-key')
        COSIGN_PUBLIC_KEY=credentials('cosign-public-key')
        DOCKER_CREDS=credentials('dockerhub-creds')
    }
    stages {
         stage('Verify Cosign') {
            steps {
                    sh 'cosign version'
                }
        }
        stage('Docker Login'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'DOCKER_CREDS', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                      sh "docker login -u $USERNAME -p $PASSWORD"
                      echo 'Login successful'
                }
            }
        }
    }
}
        
