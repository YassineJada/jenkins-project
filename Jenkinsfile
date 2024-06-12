pipeline {
    agent any
    stages {
        stage('Docker Compose') {
            agent {
                docker { image 'docker:latest' }
            }
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
        stage('Push to Docker Hub') {
            agent {
                docker { image 'docker:latest' }
            }
            steps {
                script {
                    sh 'docker login -u jada01 -p oussama123'
                    sh 'docker-compose push'
                }
            }
        }
    }
}
