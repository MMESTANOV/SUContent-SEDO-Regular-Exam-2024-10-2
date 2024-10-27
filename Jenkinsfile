pipeline {
    agent any 
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/feature-ci-pipeline']], userRemoteConfigs: [[url: 'https://github.com/MMESTANOV/SUContent-SEDO-Regular-Exam-2024-10-2']]])
            }
        }
      stages {
        stage('Restore dependencies') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                // Restore project dependencies
                bat 'dotnet restore'
            }
        }
        stage('Build project') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                // Build the project without restoring dependencies again
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                // Run tests without rebuilding, and set verbosity
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
