pipeline {
    agent any
    
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:23-alpine3.20'
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
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:23-alpine3.20'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    test -f **/.next/BUILD_ID
                '''
            }
        }
    }
}
