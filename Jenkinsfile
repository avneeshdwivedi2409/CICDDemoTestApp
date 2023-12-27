pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'dotnet restore'
                    sh 'dotnet build'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'dotnet test'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    sh 'dotnet publish -c Release -o ./publish'
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts 'publish/**/*'
        }
    }
}
