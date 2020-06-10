pipeline{
    agent any
    environment {
        GO111MODULES = 'on'
    }
    tools {
        go 'golang'
    }
    stages{
        stage{
            steps{
                sh 'go build'
            }
        }
    }
}