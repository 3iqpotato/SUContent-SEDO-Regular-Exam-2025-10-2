pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *') // проверка на всеки 1 минута
    }

    stages {
        stage('Check .NET SDK') {
            steps {
                bat 'dotnet --version'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
