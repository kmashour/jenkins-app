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

        stage('Test') {
            steps {
                echo 'Testing ...'
                sh '''
                   test -f 'static/index.html || (echo "static/index.html not found" && exit 1)'
                   npm test 
                '''
                 }

         }

    }
}