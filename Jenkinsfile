pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:6.0'
            args '-v /tmp:/tmp'  // Agar kerak bo'lsa, xost va konteyner orasida fayl tizimini ulashing
        }
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
