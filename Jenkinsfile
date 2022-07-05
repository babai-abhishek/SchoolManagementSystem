node {
    stage('Checkout') {
            echo 'checking out the application'
            deleteDir()
            checkout scm
    }
    stage('Build stage') {
            bat """
                cd .\\StudentAdmissionSystem
                dotnet build -c Release /p:Version=${BUILD_NUMBER}
                dotnet publish -c Release --no-build
                """.stripIndent().trim()
    }
    
    stage('Deploy') {
        withCredentials([usernamePassword(credentialsId: 'win-iis-cred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) { 
            bat """ 
                "C:\\Program Files (x86)\\IIS\\Microsoft Web Deploy V3\\msdeploy.exe" -verb:sync -source:iisApp="C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\dotnet-pipeline_master\\StudentAdmissionSystem\\bin\\Release\\net6.0\\publish" -enableRule:AppOffline -dest:iisApp="studentadmission",ComputerName="https://34.227.229.158:8172/msdeploy.axd",UserName="$USERNAME",Password="$PASSWORD",AuthType="Basic" -allowUntrusted
                """
            }
    }
}

