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
                sh 'java -version'
            }
        }

        stage('Check Maven Version') {
            steps {
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
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
