pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Stage 1: Build"
                echo "This stage compiles and packages the code"
                echo "Tools Used: Maven, Gradle, Apache Maven"
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo "Stage 2: Unit and Integration Tests"
                echo "Unit tests ensure the code runs as expected"
                echo "Integration tests ensure different components work together"
                echo "Tools used: JUnit, Selenium, Appium, Katalon"
            }
            post {
                success {
                    emailext attachLog: true,
                             to: "atulrane470@gmail.com",
                             subject: "Tests stage is successful.",
                             body: "Please find the attached results of the tests"
                }
                failure {
                    emailext attachLog: true,
                             to: "atulrane470@gmail.com",
                             subject: "Tests stage is unsuccessful.",
                             body: "Please find the attached log of the tests"
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo "Stage 3: Code Analysis"
                echo "External tool that analyzes if the code meets industry standards"
                echo "Tools used: SonarQube, Coverity, CodeScene"
            }
        }
        
        stage('Security Scan') {
            steps {
                echo "Stage 4: Security Scan"
                echo "Perform security scan to identify any vulnerabilities"
                echo "Tools used: Nessus, OpenVAS, ZAP"
            }
            post {
                success {
                    emailext attachLog: true,
                             to: "atulrane470@gmail.com",
                             subject: "Security scan stage is successful.",
                             body: "Please find the attached results of the scan"
                }
                failure {
                    emailext attachLog: true,
                             to: "atulrane470@gmail.com",
                             subject: "Security stage is unsuccessful.",
                             body: "Please find the attached log of the scan."
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo "Stage 5: Deploy to Staging"
                echo "Deployed the application to a AWS EC2 server"
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo "Stage 6: Integration Tests on Staging"
                echo "Running integration tests on the staging environment"
                echo "Ensure the application functions as expected in a production-like environment"
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo "Stage 7: Deploy to Production"
                echo "Deploy the application to a AWS EC2 production environment"
                echo"atul is great"
            }
        }
    }
}
