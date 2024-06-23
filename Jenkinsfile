pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
                git branch:'master', url: 'https://github.com/Thura98/Vulnerable-Web-Application.git'
            }
        }

        stage('Code Quality Check via SonarQube') {
            steps {
                script {
                def scannerHome = tool 'SonarQub';
                    withSonarQubeEnv('SonarQub') {
                    sh "ls -la"
                    }
                }
            }
        }
    }
    post {
        always {
            recordIssues enabledForFailure: true, tool: sonarQube()
        }
    }
}