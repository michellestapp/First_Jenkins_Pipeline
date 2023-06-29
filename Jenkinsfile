pipeline {
    agent any

    stages{

        stage('Test') {
            steps{
                sh 'echo "Running tests..."'
            }
        }

        stage('Build') {
            steps{
                sh 'echo "Building application"'
            }
        }

        stage('Docker') {
            steps {
                'echo "Building image and pushing to Docker Hob..."'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying application to EC2 instance..."'
            }
        }

    }
}
