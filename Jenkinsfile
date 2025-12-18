pipeline {
    agent {
        docker {
            image 'python:3.10-slim'
        }
    }
    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Check Python') {
            steps {
                sh 'python --version'
            }
        }

        stage('Create Virtualenv') {
            steps {
                sh '''
                python -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                . venv/bin/activate
                pip install -r requirementsALL.txt
                '''
            }
        }

        stage('Run Script') {
            steps {
                sh '''
                . venv/bin/activate
                python app.py
                '''
            }
        }
    }
}
