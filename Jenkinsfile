pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install API Dependencies') {
            steps {
                dir('api') {
                    bat 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('api') {
                    bat 'npm test'
                }
            }
        }

        stage('Build') {
            steps {
                dir('api') {
                    bat 'npm run build'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}