pipeline {
    agent any
    environment {
        GITHUB_CREDS=credentials('Github_creds')
        IMAGE_NAME='sriswetha06/sample-cosign'
        IMAGE_VERSION='v2'
        COSIGN_PASSWORD=credentials('cosign-password')
        COSIGN_PRIVATE_KEY=credentials('cosign-private-key')
        COSIGN_PUBLIC_KEY=credentials('cosign-public-key')
    }
    stages {
         stage('Verify Cosign') {
            steps {
                    sh 'cosign version'
                }
        }
        stage('Docker Login'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                      sh "docker login -u $USERNAME -p $PASSWORD"
                }
            }
        }
        stage('Sign and Verify image with Cosign'){
            steps{
                sh 'echo "y" | cosign sign --key $COSIGN_PRIVATE_KEY docker.io/$IMAGE_NAME:$IMAGE_VERSION'
                sh 'cosign verify --key $COSIGN_PUBLIC_KEY docker.io/$IMAGE_NAME:$IMAGE_VERSION'
                echo 'Image signed successfully'
            }
        }
        stage('Docker Logout'){
            steps{
                sh 'docker logout'
            }
        }
    }
}
        
