pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JavaUnit...'
                echo 'Running integration tests with Selenium...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Scanning for vulnerabilities with SAST scanner...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server using AWS...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server using AWS tools...'
            }
        }
    }

    post {
        success {
            // Use the emailext plugin for email with build log attachment
            emailext(
                to: "viloshanaravindu@gmail.com",
                subject: "Pipeline Success - Build # ${currentBuild.number}",
                body: "The pipeline has successfully completed all stages. Build logs are attached.",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: "viloshanaravindu@gmail.com",
                subject: "Pipeline Failure - Build # ${currentBuild.number}",
                body: "The pipeline has failed at stage ${env.STAGE_NAME}. Build logs are attached.",
                attachLog: true
            )
        }
    }
}
