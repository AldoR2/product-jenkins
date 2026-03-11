node {
    checkout scm
    // deploy env dev
    stage("Build"){
        docker.image('shippingdocker/php-composer:8.3').inside('-u root') {
            sh 'rm composer.lock'
            sh 'composer install'
        }
    }
 // Testing
    docker.image('ubuntu').inside('-u root') {
        sh 'echo "Ini adalah test"'
    }
}
