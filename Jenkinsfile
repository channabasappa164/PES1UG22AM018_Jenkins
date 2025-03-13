pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: 'main']],
                    userRemoteConfigs: [[url: 'https://github.com/channabasappa164/PES1UG22AM048_Jenkins.git']]
                ])
            }
        }

        stage('Build') {
            steps {
                build 'PES1UG22AM048-1'
                sh 'g++ main.cpp -o output'
            }
        }

        stage('Test') {
            steps {
                sh 'chmod +x output'
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }

    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
