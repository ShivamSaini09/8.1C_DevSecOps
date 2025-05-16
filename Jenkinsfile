pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube...'
            }
        }
        stage('Security Scan') {
    steps {
        script {
            if (fileExists('package.json')) {
                echo 'Running npm audit...'
                sh 'npm audit'
            } else {
                echo 'Skipping npm audit because package.json is missing.'
            }
        }
    }
}

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
            }
        }
    }
}
