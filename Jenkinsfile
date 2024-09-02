pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building project using Maven'
                // sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit and Mockito'
                // sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube'
                // sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP Dependency Check'
                // sh 'mvn dependency-check:check'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to AWS EC2 staging instance'
                // Custom script or commands
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in staging environment'
                // Custom script or commands
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to AWS EC2 production instance'
                // Custom script or commands
            }
        }
    }
    post {
        always {
            script {
                try {
                    mail to: 'sajidgoni04@gmail.com',
                         subject: "Pipeline Notification for ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                         body: "The build was ${currentBuild.currentResult}. Check console output at: ${env.BUILD_URL}",
                         attachLog: true
                } catch (Exception e) {
                    echo "Failed to send email. Error: ${e.getMessage()}"
                }
            }
        }
    }
}
