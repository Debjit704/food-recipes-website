pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Replace with your GitHub repository SSH URL
                git 'git@github.com:Debjit704/food-recipes-website.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-capstone:latest .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-creds', url: '']) {
                    sh 'docker tag devops-capstone:latest your-dockerhub-user/devops-capstone:latest'
                    sh 'docker push your-dockerhub-user/devops-capstone:latest'
                }
            }
        }
        stage('Deploy to Server') {
            steps {
                sh 'ansible-playbook -i inventory deploy.yml'
            }
        }
    }
}
