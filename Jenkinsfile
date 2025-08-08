pipeline {
    agent any

    stages {
        stage('Setup .NET SDK') {
            steps {
                sh 'dotnet --version || true'
                sh 'wget https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-6.0.412-linux-x64-binaries -O dotnet.tar.gz'
                sh 'mkdir -p $HOME/dotnet && tar zxf dotnet.tar.gz -C $HOME/dotnet'
                sh 'export PATH=$HOME/dotnet:$PATH'
            }
        }

        stage('Restore') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
