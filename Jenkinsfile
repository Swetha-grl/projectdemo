pipeline {
    agent any

    tools {
        maven 'Maven'  // Name of Maven tool configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-username/my-java-app.git', branch: 'main'
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
