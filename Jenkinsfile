pipeline {
    agent any

    stages {
        stage('Checkout Code and repository') {
            steps {
                echo 'Checking out repository...'
                git branch: 'master', url: 'https://github.com/ManarSASSI/Music-Classification-Project-.git'
            }
        }
        stage('Build frontend') {
            steps {
                script {
                    dir('frontend/music-classification-genre-')
                        {bat 'docker build -t frontend .'}
                }
            }
        }

        stage('Build svm') {
            steps {
                script {
                    dir('svm-service')
                        {bat 'docker build -t svm .'}
                }
            }
        }
        stage('Build vgg') {
            steps {
                script {
                    dir('vgg-service')
                        {bat 'docker build -t vgg .'}
                }
            }
        }
        stage('Build and Start Services with Docker Compose') {
            steps {
                script {
                        bat 'docker-compose up -d'
                }
            }
        }

        // stage('Run Tests') {
        //     steps {
        //         script {
        //             // Run tests (e.g., inside the relevant service container)
        //             if (isUnix()) {
        //                 sh 'docker-compose exec <service_name> pytest tests/'
        //             } else {
        //                 bat 'docker-compose exec <service_name> pytest tests/'
        //             }
        //         }
        //     }
        // }

        stage('Push Docker Images') {
            steps {
                script {
                    
                        bat 'docker-compose push'
                }
            }
        }

        stage('Deploy') {
            steps {
                
                echo 'Deploying app...'
            }
        }
    }
}