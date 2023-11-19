pipeline {
    agent {
        docker {
            image 'node:14' // Use the desired Node.js version
        }
    }
    environment {
        HOME = '.'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }

        stage('Run Local Test Version') {
            steps {
                script {
                    // Assuming you have a script to start your application locally
                    sh 'npm start'
                }
            }
        }

        // Add other stages as needed

    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}