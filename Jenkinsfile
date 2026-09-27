pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'docker build -t cloud-cicd-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm cloud-cicd-app python -c "import app"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker stop cloud-cicd-container || true'
                sh 'docker rm cloud-cicd-container || true'
                sh 'docker run -d --name cloud-cicd-container -p 5000:5000 cloud-cicd-app'
            }
        }

    }
}