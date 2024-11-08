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
                '''
            }
        }
        stage('Getting Environment Variables') {
            agent any
            steps {
                echo '$PATH'
                echo 'BUILD_NUMBER - $env.BUILD_NUMBER'
                echo 'BUILD_ID - $env.BUILD_ID'
                echo 'JOB_NAME - $env.JOB_NAME'
                echo 'BUILD_TAG - $env.BUILD_TAG'
                echo 'BUILD_URL - $env.BUILD_URL'
            }
        }
        stage('Test') {
            steps {
                echo'Test sstage'
            }
        }
    }
}
