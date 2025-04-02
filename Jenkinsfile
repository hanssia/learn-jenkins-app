pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                    test -f build/index.html

                '''
            }
        }
        stage('Test') {
            sh 'test -f build/index.html'
        }
    }
}
