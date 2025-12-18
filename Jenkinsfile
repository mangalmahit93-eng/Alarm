
pipeline {
    agent { label 'local1' }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "Workspace contents:"
                    ls -la
                '''
            }
        }
    }
}
