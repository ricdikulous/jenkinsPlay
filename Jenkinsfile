pipeline {
    agent { docker 'maven:3.3.3' }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
        SECRET_TEXT  = credentials('SECRET_TEXT')
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn test'
                sh 'mvn compile'
                sh 'printenv'
                sh 'ls'
                sh 'pwd'
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/**/*.xml'
        }
    }
}