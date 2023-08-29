node {
    docker.image('python:2-alpine').inside('-p 3000:3000') {
        stage('Build') {
            // checkout scm
            sh 'npm cache clean --force'
            sh 'npm install'
        }
        stage('Test') { 
            sh './jenkins/scripts/test.sh' 
        }
    }
}