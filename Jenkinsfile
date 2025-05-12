pipeline {
    agent any // Jenkins barcha agentlarida ishlashni ruxsat beradi (Docker konteynerni ishlatish uchun dockerContainerdan foydalaniladi)
    
    environment {
        // Agar kerak bo'lsa, o'zingizning environment variables'larini qo'shing
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
                // Docker konteynerda loyihani ishga tushirish
                script {
                    docker.image('mcr.microsoft.com/dotnet/aspnet:6.0').inside {
                         sh 'dotnet out/YourProjectName.dll'
                    }
                }
            }
        }
    }
    
    post {
        always {
            // Bu yerda build tugagandan keyin bajariladigan kodlarni yozishingiz mumkin
            echo 'Build tugadi!'
        }
    }
}
