pipeline {
    agent {
        docker {
            image 'node:8-alpine'
            args '-p 3000:3000 -p 5000:5000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deploy for production') {
            steps {
                sh './jenkins/scripts/deploy-for-production.sh'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
