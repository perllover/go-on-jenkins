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
                sh 'curl -s https://codecov.io/bash | bash -s -'
            }
        }
        stage('Code Analysis'){
            steps {
                sh 'curl -sfL https://install.goreleaser.com/github.comgolangci/golangci-lint.sh | bash -s -- -b $GOPATH/bin v1.17.1'
                sh 'golangci-lint run'
            }
        }
        stage ('Release') {
            when {
                buildingTag()
            }
            environment{
                GITHUB_TOKEN=credentials('123')
            }
            steps {
                sh 'curl -sL https://git.io/goreleaser | bash'
            }

        }
    }
}