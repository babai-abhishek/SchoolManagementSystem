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
                    bat 'cd .\\StudentAdmissionSystem'
                    bat 'dir'
                    bat 'msbuild /t:Package StudentAdmission.csproj'
                }
            }
        }
    }
}
