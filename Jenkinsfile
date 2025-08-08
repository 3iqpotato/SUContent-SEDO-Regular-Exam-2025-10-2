pipeline {
    agent any

    stages {
        stage('Setup .NET SDK') {
            steps {
                bat 'dotnet --version || true'
                bat 'wget https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-6.0.412-linux-x64-binaries -O dotnet.tar.gz'
                bat 'mkdir -p $HOME/dotnet && tar zxf dotnet.tar.gz -C $HOME/dotnet'
                bat 'export PATH=$HOME/dotnet:$PATH'
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
