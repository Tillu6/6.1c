pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building the code using Maven."
                // Use Maven to compile and package the code
                // sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests with JUnit and integration tests with Selenium."
                // Run unit tests with JUnit
                // sh 'mvn test'
                // Run integration tests with Selenium
                // sh 'mvn verify'
            }
            post {
                success {
                    echo "Unit and Integration Testing was successful."
                    emailext(
                        to: 'sakethreddy0014@gmail.com',
                        subject: "Tests Passed: ${currentBuild.currentResult}",
                        body: "Unit and Integration tests passed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    echo "Unit and Integration Testing failed."
                    emailext(
                        to: 'sakethreddy0014@gmail.com',
                        subject: "Tests Failed: ${currentBuild.currentResult}",
                        body: "Unit and Integration tests failed. Check the logs for details.",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Performing code analysis with SonarQube."
                // Run SonarQube analysis
                // sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo "Conducting security scan with OWASP ZAP."
                // Run OWASP ZAP security scan
                // sh 'zap-cli quick-scan http://yourapplication'
            }
            post {
                success {
                    echo "Security Scan passed."
                    emailext(
                        to: 'sakethreddy0014@gmail.com',
                        subject: "Security Scan Passed: ${currentBuild.currentResult}",
                        body: "Security scan completed successfully.",
                        attachLog: true
                    )
                }
                failure {
                    echo "Security Scan failed."
                    emailext(
                        to: 'sakethreddy0014@gmail.com',
                        subject: "Security Scan Failed: ${currentBuild.currentResult}",
                        body: "Security scan encountered issues. Check the logs for details.",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging server on AWS EC2 instance."
                // Deploy to staging server
                // sh 'scp target/yourapp.war ec2-user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Executing integration tests in staging environment."
                // Run integration tests in staging
                // sh 'mvn verify -Pstaging'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment."
                // Deploy to production server
                // sh 'scp target/yourapp.war ec2-user@production-server:/path/to/deploy'
            }
        }
    }
}
