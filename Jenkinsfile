node {
    checkout scm

    stage("Build") {
        docker.image('composer:2').inside('-u root') {
            sh 'git config --global --add safe.directory /var/jenkins_home/workspace/laravel-dev'
            sh 'composer install'
        }
    }

    stage("Test") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }

    stage("Deploy") {
        sshagent(['ssh-prod']) {
            sh 'ansible-playbook -i hosts deploy.yml'
        }
    }
}