
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading HTML source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Checking HTML project files'
                sh 'ls -la'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image'
                sh 'docker build -t my-html-website:latest .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying HTML website'
                sh '''
                    docker rm -f my-html-container || true
                    docker run -d --name my-html-container -p 8081:80 my-html-website:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully!'
        }
        failure {
            echo 'Deployment failed. Check the console output.'
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading HTML source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Checking HTML project files'
                sh 'ls -la'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image'
                sh 'docker build -t my-html-website:latest .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying HTML website'
                sh '''
                    docker rm -f my-html-container || true
                    docker run -d --name my-html-container -p 8081:80 my-html-website:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully!'
        }
        failure {
            echo 'Deployment failed. Check the console output.'
        }
    }
}
