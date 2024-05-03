pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo "Building using Gradle"
            }
        }
        stage("Unit and Integration Tests") {
            steps {
                echo "Running the unit tests with JUnit"
                echo "Running integration tests with Postman"
            }
            post {
                success {
                    emailext attachLog: true,
                    subject: "Completed both the tests",
                    body: "Completed both the tests",
                    to: "arathys630@gmail.com"  
                }
                failure {
                    emailext attachLog: true,
                    subject: "Failed both the tests",
                    body: "Failed both the tests",
                    to: "arathys630@gmail.com" 
                }
            }
        }
        stage("Code Analysis") {
            steps {
                echo "Analyzing the code quality using SonarQube"
            }
        }
        stage("Security Scan") {
            steps {
                echo "Performing security scan with OWASP ZAP"
            }
            post {
                success {
                    emailext attachLog: true,
                    subject: "Completed security scan",
                    body: "Completed security scan",
                    to: "arathys630@gmail.com"
                }
                failure {
                    emailext attachLog: true,
                    subject: "Failed security scan",
                    body: "Failed security scan",
                    to: 'arathys630@gmail.com'      
                }
            }
        }
        stage("Deploy to Staging") {
            steps {
                echo "Deploying to Staging environment using Kubernetes"
            }
        }
        stage("Integration Tests on Staging") {
            steps {
                echo "Running integration tests on Staging environment"
            }
        }
        stage("Deploy to Production") {
            steps {
                echo "Deploying to Production environment using Kubernetes"
            }
        }
    }
    post {
        success {
            emailext attachLog: true,
            subject: "Pipeline success",
            body: "Pipeline has been created successfully!",
            to: "arathys630@gmail.com"
        }
        failure {
            emailext attachLog: true,
            subject: "Pipeline failed",
            body: "The pipeline has failed. Please take necessary actions.",
            to: "arathys630@gmail.com" 
        }
    }
}
