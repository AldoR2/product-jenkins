node {

    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        docker.image('php:8.4-cli').inside {
            sh 'apt-get update'
            sh 'apt-get install -y git unzip curl'
            sh 'curl -sS https://getcomposer.org/installer | php'
            sh 'php composer.phar install'
        }
    }

    stage('Test') {
        docker.image('ubuntu').inside {
            sh 'echo "Ini adalah test"'
        }
    }

}