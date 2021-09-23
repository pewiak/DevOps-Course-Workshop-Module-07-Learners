pipeline {
    agent none
    environment {
        DOTNET_CLI_HOME = '/tmp/dotnet_cli_home'
    }

    stages {
        stage("Checkout") {
            agent any
            checkout scm
        }
        stage('Build dotnet') {
            agent { docker { image 'mcr.microsoft.com/dotnet/sdk:5.0' }
            }
            steps {
                echo 'Building..'
                dotnet build
                dir('DotnetTemplate.Web') {
                    dotnet run
                    dotnet test
                }
            }
        }
        stage('Build npm') {
            agent { docker { image 'node:14-alpine' }
            }
            steps {
                echo 'Building..'
            }
        }
    }
}