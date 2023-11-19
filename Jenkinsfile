pipeline {
    agent {
        docker {
            image 'node:14' // Use the desired Node.js version
        }
    }

    stages {
        stage('Fix npm Cache Ownership') {
            steps {
                script {
                    // Run the chown command
                    sh 'sudo chown -R 126:137 "/.npm"'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Run Dev Server') {
            steps {
                script {
                    // Run dev server with live preview
                    sh 'npm run watch'
                }
            }
        }

        stage('Build for Production') {
            steps {
                script {
                    // Make a production build
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! You may want to add additional steps or notifications here.'
        }
        failure {
            echo 'Pipeline failed! You may want to handle failure scenarios here.'
        }
    }
}