pipeline {
    agent any

    tools {
        maven 'maven'  // Name of Maven tool configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Swetha-grl/projectdemo.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // Deployment steps (can be customized)
                echo 'Deploying the application...'
            }
        }
    }

    post {
        always {
            // Archive the build artifacts
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true

            // Publish test results
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
