pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'main', url: 'https://github.com/MugeshS-04/guvidevopsday1.git'
            }
        }
        stage('build') {
            steps {
               sh "mvn clean"
               sh "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  sh 'docker build -t mugeshs04/guvidevopsday1 .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'docker-hub-cred', url: 'https://index.docker.io/v1/') {
                  sh 'docker push mugeshs04/guvidevopsday1'
               }
            }
            }
}
}
}
