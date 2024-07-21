pipeline {
    agent {
        docker {
            image 'composer:latest'
            args '--entrypoint=""'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'composer install'
            }
        }

        stage('Test') {
            steps {
                sh './vendor/bin/phpunit --log-junit logs/unitreport.xml -c tests/phpunit.xml tests'
            }
        }
    }

    post {
        always {
            junit 'logs/unitreport.xml'
        }
    }
}
