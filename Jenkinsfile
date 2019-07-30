pipeline {
    agent any

    tools {
        go 'Go 1.12.7'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mzampetakis/go-test'
            }
        }

        stage('Test') {
            steps {
                sh 'go test --cover'
            }
        }
        
        stage('Build') {
            steps {
                sh 'GOARCH=amd64 GOOS=linux go build -o go-test *.go'
            }
        }
        
        stage('Deploy') {
            steps {
                
            }
        }
    }
}