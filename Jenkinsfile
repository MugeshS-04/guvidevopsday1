pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS = credentials('docker-hub-cred')  // Docker Hub Credentials ID
    }

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/MugeshS-04/guvidevopsday1.git'
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean"
                sh "mvn install"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t mugeshs04/guvidevopsday1 .'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-cred') {
                        sh 'docker push mugeshs04/guvidevopsday1'
                    }
                }
            }
        }
    }
}

