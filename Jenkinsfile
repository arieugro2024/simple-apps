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
                cp /root/simple-apps/apps/.env apps/
                '''
            }
        }

        stage('Test Apps') {
            steps {
                sh '''
                cd apps
                npm test
                npm test:coverage
                '''
            }
        }

        stage('Scanning Code') {
            steps {
                echo "Process Scanning Code"
            }
        }


        stage('Dockerized') {
            steps {
                echo "Process Dockerized"
            }
        }

        stage('Deploy Apps') {
            steps {
                echo "Process Deploy Apps"
            }
        }

        stage('Publish') {
            steps {
                echo "Process Publish"
            }
        }

    }
}
