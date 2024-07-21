pipeline {
    agent {
        docker {
            image 'composer:latest'
            args '-u root' // Optional: adjust based on your Docker setup
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
            node {
                junit 'logs/unitreport.xml'
            }
        }
    }
}
