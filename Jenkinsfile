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
                    dir 
                    dotnet publish -c Release -r win-x64 --output C:\\inetpub\\wwwroot\\admission MySolution.sln
                    """.stripIndent().trim()
                }
            }
        }
    }
}
