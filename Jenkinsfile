Node {
    docker.image(image 'node:16-buster-slim').inside('-p 3000:3000'){
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
    }
}