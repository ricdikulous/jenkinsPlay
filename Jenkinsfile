pipeline {
    agent { docker 'maven:3.3.3' }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn test'
                sh 'mvn compile'
                sh 'printenv'
            }
        }
    }
}