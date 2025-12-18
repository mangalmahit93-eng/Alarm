pipeline {
    agent { label 'local1' }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'ls -la'
            }
        }
    }
}
