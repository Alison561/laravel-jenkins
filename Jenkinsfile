pipeline {
    agent any

    environment {
        // Variáveis de ambiente necessárias
        COMPOSER_HOME = "${WORKSPACE}/.composer"
    }

    stages {
        stage('Instalação de Dependências') {
            steps {
                // Instalar dependências do Composer
                bat 'composer install'
                // Instalar dependências do NPM
                bat 'npm install'
                // Construir os assets com o NPM
                bat 'npm run prod'
            }
        }
    }
}
