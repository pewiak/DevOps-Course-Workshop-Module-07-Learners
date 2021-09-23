pipeline {
    agent none
    environment {
        DOTNET_CLI_HOME = '/tmp/dotnet_cli_home'
    }

    stages {
        stage('Build dotnet') {
            agent { docker { image 'mcr.microsoft.com/dotnet/sdk:5.0' }
            }
            steps {
                checkout scm
                sh 'dotnet build'
                dir('DotnetTemplate.Web') {
                    sh 'dotnet run'
                    sh 'dotnet test'
                }
            }
        }
        // stage('Build npm') {
        //     agent { docker { image 'node:14-alpine' }
        //     }
        //     steps {
        //         echo 'Building..'
        //     }
        // }
    }
}