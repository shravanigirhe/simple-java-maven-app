pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven3.9'
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

        stage('Check Maven Version') {
            steps {
                bat 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Java Maven CI Pipeline SUCCESS'
        }
        failure {
            echo 'Java Maven CI Pipeline FAILED'
        }
        always {
            echo 'Pipeline execution finished'
        }
    }
}
