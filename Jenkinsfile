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

        stage('Install Python') {
            steps {
                sh '''
                if ! command -v python3 >/dev/null 2>&1; then
                  echo "Python not found. Installing..."
                  sudo apt-get update
                  sudo apt-get install -y python3 python3-venv python3-pip
                else
                  echo "Python already installed"
                fi
                python3 --version
                '''
            }
        }

        stage('Create Virtualenv') {
            steps {
                sh '''
                python3 -m venv venv
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
