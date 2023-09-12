node {
    stage('Build') {
        docker.image('python:2-alpine').inside('-p 3000:3000') {
            sh 'python -m py_compile sources/add2vals.py sources/calc.py'
        }
    }
    stage('Test') { 
        docker.image('qnib/pytest').inside('-p 3000:3000') {
            sh 'py.test --verbose --junit-xml test-reports/results.xml sources/test_calc.py'
        }
    }
    stage('Manual Approval') {
        input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk melanjutkan eksekusi pipeline ke tahap Deploy atau Klik "Abort" untuk menghentikan eksekusi pipeline)' 
    }
    stage('Deploy') {
        env.VOLUME = "${pwd()}/sources:/src"
        env.IMAGE = 'cdrx/pyinstaller-linux:python2'
        dir(env.BUILD_ID) {
            sh "docker run --rm -v ${env.VOLUME} ${env.IMAGE} 'pyinstaller -F add2vals.py'"
        }
        // archiveArtifacts "sources/dist/add2vals"
        // sh "docker run --rm -v ${env.VOLUME} ${env.IMAGE} 'rm -rf build dist'"
    }
}