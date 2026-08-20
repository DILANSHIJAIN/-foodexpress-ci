pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat '''
                    "C:\\Users\\dilan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m venv venv
                    call venv\\Scripts\\activate.bat
                    pip install pytest flake8
                '''
            }
        }
        stage('Code Quality') {
            steps {
                bat '''
                    call venv\\Scripts\\activate.bat
                    flake8 cart.py orders.py || exit 0
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                    call venv\\Scripts\\activate.bat
                    pytest
                '''
            }
        }
        stage('Package') {
            steps {
                bat '''
                    call venv\\Scripts\\activate.bat
                    python package.py
                '''
                archiveArtifacts artifacts: 'foodexpress.zip', fingerprint: true
            }
        }
    }
    post {
        success {
            echo 'SUCCESS: all stages passed and the artifact was created.'
        }
        failure {
            echo 'FAILURE: one stage failed. Open the red stage to see why.'
        }
    }
}