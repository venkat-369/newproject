pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/your-repo/html-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t my-html-app .'
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // First stop any old container
                    sh '''
                    docker ps -q --filter "name=my-html-app" | grep -q . && docker stop my-html-app && docker rm my-html-app || true
                    '''

                    // Run new container
                    sh 'docker run -d -p 8080:80 --name my-html-app my-html-app'
                }
            }
        }
    }
}
