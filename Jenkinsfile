pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *') // Poll every 5 minutes
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency Check...'
                sh './dependency-check.sh --project my-app --scan ./'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging Environment...'
                sh 'scp target/my-app.jar ec2-user@staging-server:/opt/app'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                sh 'newman run postman_collection.json'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production Environment...'
                sh 'scp target/my-app.jar ec2-user@production-server:/opt/app'
            }
        }

    }
}
