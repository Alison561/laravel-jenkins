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

        stage('subir a aplicacao'){
            steps{
                bat 'php artisan serve'
            }
        }

        stage('Test') {
            steps {
                bat 'start /B php artisan serve --host=0.0.0.0 --port=8000'
                sleep 5
            }
        }
    }
}
