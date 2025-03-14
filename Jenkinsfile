pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/shobithps/PES1UG22CS564_Jenkins.git']]])
            }
        }
        
        stage('Build') {
            steps {
                build 'PES1UG22CS595-1'
                sh 'g++ ./main/hello1.cpp -o output'
            }
        }

        stage('Test') {
            steps {
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
change necessary details
