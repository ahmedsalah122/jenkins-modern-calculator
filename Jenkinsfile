pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Virtual Environment') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                python -m pip install --upgrade pip
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                . venv/bin/activate
                pip install -r requirements.txt || true
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                python -m py_compile *.py
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                . venv/bin/activate
                nohup python main.py > output.log 2>&1 &
                '''
            }
        }
    }
}