node {
    checkout scm
    docker.image('python:2-alpine').inside('-p 3000:3000') {
        stage('Build') {
            sh 'npm install'
        }

        // stage('Test') { 
        //     sh './jenkins/scripts/test.sh' 
        // }
    }
}