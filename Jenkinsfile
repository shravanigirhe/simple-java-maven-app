pipeline {
    agent any

    environment {
        JAVA_HOME  = "C:\\Program Files\\Java\\jdk-21.0.10"
        MAVEN_HOME = "C:\\apache-maven-3.9.6"
        PATH = "${env.JAVA_HOME}\\bin;${env.MAVEN_HOME}\\bin;${env.PATH}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Check Java Version') {
            steps {
                bat '"%JAVA_HOME%\\bin\\java.exe" -version'
            }
        }

        stage('Check Maven Version') {
            steps {
                bat '"%MAVEN_HOME%\\bin\\mvn.cmd" -version'
            }
        }

        stage('Build') {
            steps {
                bat '"%MAVEN_HOME%\\bin\\mvn.cmd" clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                bat '"%MAVEN_HOME%\\bin\\mvn.cmd" test'
            }
        }

        stage('Package') {
            steps {
                bat '"%MAVEN_HOME%\\bin\\mvn.cmd" package'
            }
        }
    }

    post {
        success {
            echo "✅ Java Maven CI Pipeline SUCCESS"
        }
        failure {
            echo "❌ Java Maven CI Pipeline FAILED"
        }
    }
}
