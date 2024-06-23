pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
               echo "Build - 1"
            }
        }

        stage('Secrets Scanning') {
            steps {
               echo "Started Secrets scanning uisng gitleaks"
                sh "gitleaks --exit-code 0 detect . -v --no-git -f json -r secretsScanning.json"
            }
        }
        stage('Dependency Scanning') {
            steps {
               echo "Started Dependency scanning uisng Trivy"
                sh "trivy -q repo . -f json -o trivy_report.json"
            }
        }

        stage('Secrets Scanning Docker') {
            agent {
                any { image 'zricethezav/gitleaks' }
            }
            steps {
                sh 'docker run -v .:/path zricethezav/gitleaks:latest detect . -v --no-git -f json -r secretsScanning1.json --source="/path" '
            }
        }
        stage('Test') {
            steps {
                 echo "Test"
            }
        }
        stage('Deploy') {
            steps {
                 echo "Deploy"
            }
        }
    }
}
