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
    }
}