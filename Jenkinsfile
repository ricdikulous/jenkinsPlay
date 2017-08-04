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
    }
    post {
        always {
            junit 'generated-test-sources/surefire-reports/**/*.xml'
        }
    }
}