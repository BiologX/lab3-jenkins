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
                sh 'echo "Build step completed"'
            }
        }
    }
}

// Простое ветвление для 3 веток
if (env.BRANCH_NAME == 'development') {
    pipeline {
        stages {
            stage('Dev Tests') {
                steps {
                    echo 'Running development tests'
                    sh 'python hello.py'
                }
            }
        }
    }
} else if (env.BRANCH_NAME == 'staging') {
    pipeline {
        stages {
            stage('Staging Tests') {
                steps {
                    echo 'Running staging tests'
                    sh 'python hello.py && echo "Staging tests passed"'
                }
            }
        }
    }
} else if (env.BRANCH_NAME == 'production') {
    pipeline {
        stages {
            stage('Production Deploy') {
                steps {
                    echo 'Deploying to production'
                    sh 'python hello.py && echo "PRODUCTION DEPLOY COMPLETE"'
                }
            }
        }
    }
} else {
    echo "Unknown branch: ${env.BRANCH_NAME}"
}