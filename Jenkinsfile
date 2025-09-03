pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/venkat-369/newproject.git',
                    credentialsId: 'newproject'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t newproject:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker rm -f newproject || true
                  docker run -d -p 8080:80 --name newproject newproject:latest
                '''
            }
        }
    }
}
