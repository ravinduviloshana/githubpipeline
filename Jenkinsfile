pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Fetching source code from GitHub...'
                // Normally, you'd use: checkout scm
            }
        }
        
        stage('Tool Install') {
            steps {
                echo 'Installing necessary build tools...'
                // This is where Maven or other tools would be installed if needed
            }
        }

        stage('Build') {
            steps {
                echo "Running Maven..."
                echo "Building Code..."
                sleep 15
                echo "Maven build completed successfully."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests..."
                sleep 5
                echo "Simulating: mvn test"
            }
            post {
                success {
                    emailext(
                        to: 'viloshanaravindu@gmail.com',
                        subject: "Pipeline - Unit and Integration Tests SUCCESS: ${currentBuild.fullDisplayName}",
                        body: "The unit and integration test completed successfully. Please find the logs attached.",
                        attachLog: true, compressLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'viloshanaravindu@gmail.com',
                        subject: "Pipeline - Unit and Integration Tests FAILURE: ${currentBuild.fullDisplayName}",
                        body: "The unit and integration test failed. Please find the logs attached.",
                        attachLog: true, compressLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP Dependency Check...'
                sleep 25
                echo 'OWASP: Codebase and dependencies have no active vulnerabilities.'
            }
            post {
                success {
                    emailext(
                        to: 'viloshanaravindu@gmail.com',
                        subject: "Pipeline - Security Scan SUCCESS: ${currentBuild.fullDisplayName}",
                        body: "The security scan completed successfully. Please find the logs attached.",
                        attachLog: true, compressLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'viloshanaravindu@gmail.com',
                        subject: "Pipeline - Security Scan FAILURE: ${currentBuild.fullDisplayName}",
                        body: "The security scan failed. Please find the logs attached.",
                        attachLog: true, compressLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                sleep 10
                echo 'Simulating: deployment to AWS EC2 (staging)'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                sleep 7
                echo 'Simulating: integration tests on staging server'
            }
            post {
                success {
                    emailext(
                        to: 'viloshanaravindu@gmail.com',
                        subject: "Pipeline - Integration Tests on Staging SUCCESS: ${currentBuild.fullDisplayName}",
                        body: "Integration tests on staging completed successfully. Please find the logs attached.",
                        attachLog: true, compressLog: true
                    )
                }
                failure {
                    emailext(
                        to: 'viloshanaravindu@gmail.com',
                        subject: "Pipeline - Integration Tests on Staging FAILURE: ${currentBuild.fullDisplayName}",
                        body: "Integration tests on staging failed. Please find the logs attached.",
                        attachLog: true, compressLog: true
                    )
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment using Kubernetes...'
                sleep 20
                echo 'Production deployment completed successfully.'
            }
        }
    }

    post {
        always {
            echo 'Sending final email notification...'
            emailext(
                to: 'viloshanaravindu@gmail.com',
                subject: "Pipeline finished: ${currentBuild.fullDisplayName}",
                body: "Check console output at ${env.BUILD_URL}"
            )
        }
    }
}
