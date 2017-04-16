#!/usr/bin/env groovy

node('master') {
    try {
        stage('build') {
            checkout scm

            sh "composer install"
            sh "cp .env.example .env"
            sh "php artisan key:generate"
        }

        stage('test') {
            sh "./vendor/bin/phpunit"
        }

        stage('deploy') {
            // ansible-playbook -i ./ansible/hosts ./ansible/deploy.yml
            sh "echo 'WE ARE DEPLOYING'"
        }
    } catch(error) {
        throw error
    } finally {

    }

}