pipeline {
    agent {
        node{
            label 'devops-arie'
        }
    }

    stages {
        stage('Build Apps') {
            steps {
                sh '''
                cd apps
                npm install
                '''
            }
        }

        stage('Copy ENV') {
            steps {
                sh '''
                sudo cp /root/simple-apps/apps/.env apps/
                '''
            }
        }

        stage('Test Apps') {
            steps {
                sh '''
                cd apps
                npm test
                npm run test:coverage
                '''
            }
        }

        stage('Scanning Code') {
            steps {
                sh '''
                cd apps
                sonar-scanner   -Dsonar.projectKey=Simple-Apps   -Dsonar.sources=.   -Dsonar.host.url=http://172.23.2.32:9000   -Dsonar.login=sqp_740c2c70fd3dd8ea72a8b503f95743661e8ed740
                '''
            }
        }


        stage('Dockerized') {
            steps {
                sh '''
                docker compose build
                '''
            }
        }

        stage('Deploy Apps') {
            steps {
                sh '''
                docker compose up -d
                '''
            }
        }

        stage('Publish') {
            steps {
                sh '''
                docker compose push
                '''
            }
        }

    }
}
