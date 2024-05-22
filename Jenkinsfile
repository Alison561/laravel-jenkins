pipeline {
    agent any

    environment {
        COMPOSER_HOME = "${WORKSPACE}/.composer"
        DB_CONNECTION = 'pgsql'
        DB_DATABASE = 'laravel_jenkins'
        DB_USERNAME = 'postgres'
        DB_PASSWORD = 'Swporte@01'
    }

    stages {
        stage('Build') {
            steps {
                bat 'composer install'
                bat 'npm install'
                bat 'npm run build'
            }
        }
        stage('Configuração do Ambiente') {
            steps {
                bat 'copy .env.example .env'
                bat 'php artisan key:generate'
                powershell '''
                   (Get-Content .env) -replace 'DB_CONNECTION=.*', 'DB_CONNECTION=$env:DB_CONNECTION' | Set-Content .env
                   (Get-Content .env) -replace 'DB_DATABASE=.*', 'DB_DATABASE=$env:DB_DATABASE' | Set-Content .env
                   (Get-Content .env) -replace 'DB_USERNAME=.*', 'DB_USERNAME=$env:DB_USERNAME' | Set-Content .env
                   (Get-Content .env) -replace 'DB_PASSWORD=.*', 'DB_PASSWORD=$env:DB_PASSWORD' | Set-Content .env
                '''
            }
        }

        stage('Iniciar Servidor') {
            steps {
                 bat 'start /B php artisan serve --host=0.0.0.0 --port=8000'
                sleep 15
            }
        }

        stage('teste') {
            steps {
                 bat 'php artisan test'
            }
        }
    }
}
