node {
    stage('Checkout') {
            echo 'checking out the application'
            deleteDir()
            checkout scm
    }
    stage('Build stage') {
            bat """
                cd .\\StudentAdmissionSystem
                dotnet restore
                dotnet publish StudentAdmission.csproj
                """.stripIndent().trim()
    }
}

