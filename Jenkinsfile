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
                sh 'composer install'
                // Instalar dependências do NPM
                sh 'npm install'
                // Construir os assets com o NPM
                sh 'npm run prod'
            }
        }
    }
}
