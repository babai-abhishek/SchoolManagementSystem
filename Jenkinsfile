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
                    bat 'dir'
                    bat 'dotnet restore'
                    bat 'dotnet msbuild .\\StudentAdmissionSystem\\StudentAdmission.csproj'
                }
            }
        }
    }
}
