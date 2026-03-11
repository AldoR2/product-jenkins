node {

    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        docker.image('composer:2-php8.3').inside('--user root') {
            sh 'composer install --no-interaction --prefer-dist'
        }
    }

    stage('Test') {
        docker.image('ubuntu').inside('--user root') {
            sh 'echo "Ini adalah test"'
        }
    }

}