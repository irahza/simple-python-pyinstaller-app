node {
    docker.image('python:2-alpine').inside('-p 3000:3000') {
        stage('Build') {
            // checkout scm
            sh 'python -m py_compile sources/add2vals.py sources/calc.py'
        }
        // stage('Test') { 
        //     sh './jenkins/scripts/test.sh' 
        // }
    }
}