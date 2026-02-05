pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-21'
        MVN_CMD   = 'C:\\Program Files\\Apache\\Maven\\bin\\mvn.cmd'
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Check Java Version') {
            steps {
                bat "\"%JAVA_HOME%\\bin\\java.exe\" -version"
            }
        }

        stage('Check Maven Version') {
            steps {
                bat "\"%MVN_CMD%\" -version"
            }
        }

        stage('Build') {
            steps {
                bat "\"%MVN_CMD%\" clean compile"
            }
        }

        stage('Run Tests') {
            steps {
                bat "\"%MVN_CMD%\" test"
            }
        }

        stage('Package') {
            steps {
                bat "\"%MVN_CMD%\" package"
            }
        }
    }

    post {
        success {
            echo '✅ Java 21 CI Pipeline SUCCESS'
        }
        failure {
            echo '❌ Java 21 CI Pipeline FAILED'
        }
    }
}
