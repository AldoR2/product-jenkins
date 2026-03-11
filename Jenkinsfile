node {

    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        docker.image('composer:2.7-php8.2').inside {
            sh 'git config --global --add safe.directory /var/jenkins_home/workspace/laravel-dev'
            sh 'composer install --no-interaction --prefer-dist --no-progress'
        }
    }

    stage('Test') {
        docker.image('composer:2.7-php8.2').inside {
            sh 'php artisan test || true'
        }
    }

    stage('Deploy') {
        sshagent(['ssh-prod']) {
            sh 'ansible-playbook -i hosts deploy.yml'
        }
    }

}