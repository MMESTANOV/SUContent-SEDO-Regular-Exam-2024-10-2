pipeline {
    agent any 
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/feature-ci-pipeline']], userRemoteConfigs: [[url: 'https://github.com/MMESTANOV/SUContent-SEDO-Regular-Exam-2024-10-2']]])
            }
        }
        stage('Restore dependencies') { 
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Dotnet Build') { 
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') { 
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
