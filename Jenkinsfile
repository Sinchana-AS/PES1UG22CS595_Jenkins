pipeline {
    agent any  // Use any agent that supports the docker command

    stages {
        stage('Clone repository') {
            steps {
                git branch: 'main', url: 'https://github.com/cusery/crepo.git'
            }
        }
        stage('Install dependencies') {
            steps {
                script {
                    docker.image('node:14').inside {
                        sh 'npm install'
                    }
                }
            }
        }
        stage('Build application') {
            steps {
                script {
                    docker.image('node:14').inside {
                        sh 'npm run build'
                    }
                }
            }
        }
        stage('Test application') {
            steps {
                script {
                    docker.image('node:14').inside {
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Push Docker image') {
            steps {
                script {
                    docker.image('node:14').inside {
                        sh 'docker build -t <user>/<image>:$BUILD_NUMBER .'
                        sh 'docker push <user>/<image>:$BUILD_NUMBER'
                    }
                }
            }
        }
    }
}
