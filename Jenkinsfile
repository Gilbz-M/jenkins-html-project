
pipeline {
    agent any

    options {
        disableConcurrentBuilds()
        skipDefaultCheckout(true)
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Downloading project from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Checking HTML project files'
                sh '''
                    echo "Checking index.html..."
                    test -f index.html
                    echo "HTML file found successfully!"
                    ls -la
                '''
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building website Docker image'
                sh '''
                    docker build -t my-html-website:latest .
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website using Nginx'

                sh '''
                    docker rm -f my-html-container || true

                    sleep 2

                    docker run -d \
                        --restart unless-stopped \
                        --name my-html-container \
                        -p 8081:80 \
                        my-html-website:latest

                    echo "Website deployment completed!"
                    docker ps --filter name=my-html-container
                '''
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: CI/CD pipeline completed!'
            echo 'Website is available at http://localhost:8081'
        }

        failure {
            echo 'FAILED: Please check the Console Output.'
        }

        always {
            echo 'Jenkins pipeline execution finished.'
        }
    }
}
