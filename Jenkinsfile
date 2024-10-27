pipeline {
    agent any

    stages {
        stage('Restore dependencies') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build project') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
