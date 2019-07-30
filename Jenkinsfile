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
                sh 'go get github.com/sirupsen/logrus'
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
                withCredentials([string(credentialsId: "thesecret", variable: 'MY_SECRET')]) {
                sh 'echo Deploying with secret:'
                sh 'echo $MY_SECRET'
                }
            }
        }
    }
}
