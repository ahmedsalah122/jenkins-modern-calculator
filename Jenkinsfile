pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                 checkout scm
            }
        }   

        stage('Build') {
            steps {
                sh 'python3 -m pip install --upgrade pip'
                sh 'pip3 install -r requirements.txt || true'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m py_compile *.py'
            }
        }

        stage('Deploy') {
            steps {
                sh 'nohup python3 main.py > output.log 2>&1 &'
            }
        }
    }
}