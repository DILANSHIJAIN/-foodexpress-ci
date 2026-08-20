pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat '"C:\\Users\\dilan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pip install pytest'
            }
        }
        stage('Test') {
            steps {
                bat '"C:\\Users\\dilan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pytest'
            }
        }
    }
}