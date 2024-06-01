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
                sh "gitleaks detect . -v --no-git -f json -r secretsScanning.json"
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
