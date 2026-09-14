pipeline {
    agent any
    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/nai1551/react.git'
            }
        }

        stage('Verify Node and Yarn') {
            steps {
                sh '''
                    node --version
                    yarn --version
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'yarn install --frozen-lockfile'
            }
        }

        stage('Run tests') {
            steps {
                sh 'yarn test --ci'
            }
        }

        stage('Build') {
            steps {
                sh 'yarn build'
            }
        }
    }

    post {
        success {
            echo 'React library build succeeded!'
        }
        failure {
            echo 'React library build failed!'
        }
    }
}