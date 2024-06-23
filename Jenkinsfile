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
                def scannerHome = tool 'SonarQube';
                    withSonarQubeEnv('SonarQube') {
                    // sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWASP - Dsonar.sources=. -Dsonar.host.url=http://192.168.18.16:9000 -Dsonar.token=sqp_240780fb5554e4b40f916c4800adec6026ac197a"
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