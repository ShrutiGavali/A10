pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Checkout source code from GitHub
                checkout([$class: 'Git', branches: [[name: '*/main']], 
                          userRemoteConfigs: [[url: 'https://github.com/yourusername/your-repo.git']]])

                // Build Docker image
                script {
                    def dockerImage = docker.build('java1-docker:latest', '-f Dockerfile .')
                }
            }
        }
        stage('Push') {
            steps {
                // Push Docker image to Docker Hub (change as per your registry)
                script {
                    docker.withRegistry('https://registry.example.com', 'docker-credentials-shrutigavali') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
