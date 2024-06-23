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
                sh "trivy repo . -f json -r DependencyScanning.json"
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
