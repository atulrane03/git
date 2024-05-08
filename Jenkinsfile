pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Build in progress..."
                echo "This stage compiles and packages the code"
                echo "Tools Used: CircleCI, Gradle, Apache Maven"
                echo "Build complete..."
            }
        }
        stage('Unit and Integrations Tests') {
            steps {
                echo 'Unit and integration tests ensure that the code runs as expected'
                echo 'Tools used: Selenium, Appium, Katalon'
            }
            post {
                success {
                    emailext attachLog: true,
                    to: "$TEST_EMAIL_RECEPIENT",
                    subject: "Tests stage is successfull.",
                    body: "Please find the attached results of the tests"
                }
                failure {
                    emailext attachLog: true,
                    to: "$TEST_EMAIL_RECEPIENT",
                    subject: "Tests stage is unsuccessfull.",
                    body: "Please find the attached log of the tests "
                }
                }
        }
        stage('Code Analysis') {
            steps {
                echo 'External tool that analyze if the code meets the industry standards '
                echo 'Tools used: SonarQube, Coverity, CodeScene'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Perform security scan to identify any vulnerabilities'
                echo 'Tools used: Nessus, OpenVAS'
            }
            post {
                success {
                    emailext attachLog: true,
                    to: "$SECURITY_SCAN_EMAIL_RECEPIENT",
                    subject: "Security scan stage is successfull.",
                    body: "Please find the attached results of the scan"
                }
                failure {
                    emailext attachLog: true,
                    to: "$SECURITY_SCAN_EMAIL_RECEPIENT",
                    subject: "Security stage is unsuccessfull.",
                    body: "Please find the attached log of the scan."
                }
                }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Waiting for approval'
                sleep 10
                echo 'Approval Received'
                echo "Deployed to staging AWS EC2 server: $STAGING_ENVIRONMENT"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration test on staging environment to ensure the application 
functions as expected"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploy application to a AWS EC2 production environment: 
$PRODUCTION_ENVIRONMENT"
            }
        }
    }
