pipeline {
    agent any

    stages {
       
        stage('Docker Build') {
            steps {
                script {
                    bat 'docker build -t server:latest ./server'
                    bat 'docker build -t client:latest ./client'                
                }
            }
        }
       
        stage('Docker Push client') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-repo'){
                        bat 'docker tag client:latest jada01/front_end'
                        bat 'docker push jada01/front_end'
                    }
                }
            }
        }
       
        stage ('Docker Push server') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-repo') {
                        bat 'docker tag server:latest jada01/back_end'
                        bat 'docker push jada01/back_end'
                    }
                }
            }
        }
    }
}
