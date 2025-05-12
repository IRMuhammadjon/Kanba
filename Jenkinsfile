pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/aspnet:6.0' // Docker image, .NET Core 6.0 uchun
            args '-p 8080:80' // Portni konteynerga ulash
        }
    }
    environment {
        // Agar kerak bo‘lsa, bu yerga o‘zingizning environment variables’larini qo‘shing
    }
    stages {
        stage('Checkout') {
            steps {
                // Git reposidan kodni olish
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // .NET Core build qilish
                script {
                    sh 'dotnet build'
                }
            }
        }
        stage('Publish') {
            steps {
                // .NET Core publish qilish
                script {
                    sh 'dotnet publish -c Release -o out'
                }
            }
        }
        stage('Run') {
            steps {
                // Docker konteyner ichida run qilish
                script {
                    sh 'dotnet out/Kanba.dll'
                }
            }
        }
    }
    post {
        always {
            // Build tugagandan keyin bajariladigan operatsiyalar (masalan, tozalash)
        }
    }
}
