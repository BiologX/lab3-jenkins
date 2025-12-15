pipeline {
    agent any
    
    // Добавляем параметр выбора
    parameters {
        choice(
            name: 'BRANCH',
            choices: ['development', 'staging', 'production'],
            description: 'Для лабораторной: выберите одну из 3 веток'
        )
    }
    
    stages {
        stage('Лабораторная работа №3') {
            steps {
                echo "Конвейер непрерывной интеграции Jenkins"
                echo "Выбрана ветка: ${params.BRANCH}"
            }
        }
        
        stage('Этап 1: Проверка кода') {
            steps {
                bat 'echo "Проверка кода для ветки ${params.BRANCH}"'
            }
        }
        
        stage('Этап 2: Сборка') {
            steps {
                script {
                    switch(params.BRANCH) {
                        case 'development':
                            bat 'echo "Сборка DEV версии"'
                            break
                        case 'staging':
                            bat 'echo "Сборка STAGING версии"'
                            break
                        case 'production':
                            bat 'echo "Сборка PRODUCTION версии"'
                            break
                    }
                }
            }
        }
        
        stage('Этап 3: Деплой') {
            steps {
                bat 'echo "Деплой завершен успешно!"'
                echo "Лабораторная работа №3 выполнена"
                echo "Репозиторий: https://github.com/BiologX/lab3-jenkins"
                echo "Ветки: development, staging, production"
            }
        }
    }
}