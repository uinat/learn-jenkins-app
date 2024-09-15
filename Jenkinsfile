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
        stage('Test') {
            steps {
                sh '''
                    if [ -f build/index.html ]; then
                        echo "The file build/index.html exists."
                    else
                        echo "The file build/index.html does not exist."
                    fi
                '''
            }
        }
    }
}