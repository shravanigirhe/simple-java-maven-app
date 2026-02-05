pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-21.0.10'
        PATH = "${JAVA_HOME}\\bin;${env.PATH}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Check Java Version') {
            steps {
                bat 'java -version'
            }
        }

        stage('Build') {
            steps {
                bat 'mvnw.cmd clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'mvnw.cmd test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvnw.cmd package'
            }
        }
    }

    post {
        success {
            echo '✅ Java 21 CI Pipeline SUCCESS (No Maven errors)'
        }
        failure {
            echo '❌ Java 21 CI Pipeline FAILED'
        }
    }
}
