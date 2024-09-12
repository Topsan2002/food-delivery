pipeline {
    agent any
    environment {
          AWS_REGION = 'ap-southeast-1'  // Replace with your region
          AWS_ACCOUNT_ID = credentials('AWS_ACCOUNT_ID')
          ECR_REPO_NAME = 'food-delivery-discovery-service'  // Replace with your ECR repository name
          IMAGE_TAG = "${env.BUILD_ID}"  // Or use 'latest' or any other tag
          WORKSPACE = "/var/lib/jenkins/workspace/food-delivery-compose"
    }
    stages {
        stage('Clone Repo to Build') {
            steps {
                git url: 'https://github.com/Topsan2002/food-delivery-compose.git',
                    branch:'main'
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker-compose down"
                    sh "docker-compose up -d --build"
                    // sh "docker info"
                    // sh "curl --version"
                    // sh "jq --version"
                }
            }
        }
    }
}