pipeline {
    agent {
        dockerContainer 'mcr.microsoft.com/dotnet/sdk:6.0'  // Docker imidjini to'g'ri kiriting
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'dotnet build'
            }
        }
        stage('Publish') {
            steps {
                sh 'dotnet publish -c Release -o out'
            }
        }
        stage('Run') {
            steps {
                sh 'dotnet out/YourProjectName.dll'
            }
        }
    }
    
    post {
        always {
            echo 'Build tugadi!'
        }
    }
}
