pipeline {
    agent any

    environment {
        registry = "532026769849.dkr.ecr.us-west-2.amazonaws.com/bmw"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/gustaaavolucas/desafio']])
            }
        }
        
        stage ("Build JAR") {
            steps {
                sh "mvn clean install"
            }
        }
        
        stage ("Build Image") {
            steps {
                script {
                    docker.build registry
                }
            }
        }
        
        stage ("Push to ECR") {
            steps {
                script {
                    sh "aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 532026769849.dkr.ecr.us-west-2.amazonaws.com"
                    sh "docker push 532026769849.dkr.ecr.us-west-2.amazonaws.com/bmw:$BUILD_NUMBER"
                    
                }
            }
        }
        
        stage ("Helm Deploy") {
            steps {
                script {
                      sh "helm upgrade first --install helm-chart --namespace helm-deployment --set image.tag=$BUILD_NUMBER"
                }
            }
        }
    }
}