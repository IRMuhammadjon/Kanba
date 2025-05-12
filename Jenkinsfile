pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:6.0'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'dotnet --version'
            }
        }
    }
}
