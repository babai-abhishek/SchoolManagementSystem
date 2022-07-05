pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'checking out the application'
                deleteDir()
                checkout scm
            }
        }
        stage('Build stage') {
            steps {
                script{
                 //   bat 'cd /D .\\StudentAdmissionSystem'
                 //   bat 'dir'
                 //   bat 'dotnet restore'
                 //   bat 'dotnet msbuild .\\StudentAdmissionSystem\\StudentAdmission.csproj'
                bat """
                    cd .\\StudentAdmissionSystem
                    dotnet build -c Release /p:Version=${BUILD_NUMBER}
                    dotnet publish -c Release --no-build
                    """.stripIndent().trim()
                }
            }
        }
    }
}
