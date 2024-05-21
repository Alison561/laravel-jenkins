pipeline {
    agent any

    environment {
        // Variáveis de ambiente necessárias
        COMPOSER_HOME = "${WORKSPACE}/.composer"
    }

    stages {
        stage('Build') {
            steps {
                // Instalar dependências do Composer
                bat 'composer install'
                // Instalar dependências do NPM
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                bat 'php artisan test'
            }
        }
    }
}
