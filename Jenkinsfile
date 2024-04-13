pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                // Clone repository
                git 'https://github.com/beniye19/gallery'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install required software
                sh 'npm install'
            }
        }

        stage('Deploy to Render') {
            steps {
                // Deploy to Render
                sh 'npm run deploy'
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests
                sh 'npm test'
            }
        }

        stage('Notify Slack') {
            steps {
                // Send Slack notification on successful deploy
                slackSend channel: 'bensonmwangi_ip1', color: 'good', message: "Build #${env.BUILD_NUMBER} deployed successfully. View at: ${env.RENDER_URL}"
            }
        }
    }

    post {
        always {
            // Cleanup steps, if any
        }

        success {
            // Additional actions on successful deployment
        }

        failure {
            // Additional actions on failed deployment
        }
    }
}
