stage('Install Cosign') {
  steps {
    sh '''
      # Download Cosign binary
      curl -L https://github.com/sigstore/cosign/releases/download/v1.2.2/cosign-v1.2.2-linux-amd64.gz -o cosign.gz

      # Uncompress the archive
      gunzip cosign.gz

      # Move the binary to a bin directory (adjust path if needed)
      sudo mv cosign /usr/local/bin/cosign

      # Make the binary executable
      sudo chmod +x /usr/local/bin/cosign

      # Cosign version
      sudo cosign version
    '''
  }
}
