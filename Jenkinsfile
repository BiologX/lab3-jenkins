pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from Git'
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building project...'
                // Для Windows используем bat вместо sh
                bat 'echo "Build step completed on Windows"'
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Определяем поведение для разных веток
                    if (env.BRANCH_NAME == 'master' || env.BRANCH_NAME == 'main') {
                        echo "Running main branch pipeline"
                        bat 'echo "Main branch tests"'
                    } else if (env.BRANCH_NAME == 'development') {
                        echo "Running development branch pipeline"
                        bat 'echo "Development tests"'
                    } else if (env.BRANCH_NAME == 'staging') {
                        echo "Running staging branch pipeline"
                        bat 'echo "Staging tests"'
                    } else if (env.BRANCH_NAME == 'production') {
                        echo "Running production branch pipeline"
                        bat 'echo "Production deployment"'
                    } else {
                        echo "Unknown branch: ${env.BRANCH_NAME}"
                        bat 'echo "Default pipeline"'
                    }
                }
            }
        }
        
        stage('Final') {
            steps {
                bat 'dir'  // Показать содержимое директории
                echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
            }
        }
    }
    
    post {
        always {
            echo "Pipeline finished"
        }
        success {
            echo "SUCCESS!"
        }
        failure {
            echo "FAILED!"
        }
    }
}