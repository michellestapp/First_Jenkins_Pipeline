pipeline {
    agent any

    stages{

        stage('Test') {

            steps{

                script{
                    def nodejsTool = tool name:'node-20-tool', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodejsTool}/bin:${env.PATH}"
                }

                sh 'node --version'
                sh 'echo "Running tests..."'
            }
        }

        stage('Build') {
            
            steps{

                script {
                    def dockerTool = tool name: 'docker-latest-tool', type: 'org.jenkinsci.plugins.docker.commons.tools.DockerTool'
                    env.PATH = "${dockerTool}/bin:${env.PATH}"
                }
                sh "docker --version"
                sh 'echo "Building application..."'
            }
        }

        stage('Docker') {
            steps {

                withCredentials([usernamePassword(credentialsId: 'personal-docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]){
                    sh 'echo "Username: $DOCKER_USERNAME"'
                }
                sh 'echo "Building image and pushing to Docker Hob..."'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying application to EC2 instance..."'
            }
        }

    }
}
