pipeline{
    agent any
    environment {
        GO111MODULES = 'on'
    }
    tools {
        go 'golang'
    }
    stages{
        stage('Build'){
            steps{
                sh 'go build'
            }
        }
        stage('Test'){
            environment {
                CODECOVE_TOKEN = credentials('123')
            }
            steps {
                sh 'go test ./... -coverprofile=coverage.txt'
                sh curl -s https://codecov.io/bash | bash -s -''
            }
        }
    }
}