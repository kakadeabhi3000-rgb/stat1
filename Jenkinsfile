
pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nginx-static-site .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                    docker rm -f static-nginx || true
                    docker run -d --name static-nginx -p 80:80 nginx-static-site
                '''
            }
        }
    }
}
