pipeline {
    agent any

    environment {
        JAVA = 'C:\\Program Files\\Java\\jdk-21.0.10\\bin\\java.exe'
        JAVAC = 'C:\\Program Files\\Java\\jdk-21.0.10\\bin\\javac.exe'
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Check Java Version') {
            steps {
                bat "\"%JAVA%\" -version"
            }
        }

        stage('Compile Java') {
            steps {
                bat '''
                if not exist out mkdir out
                "%JAVAC%" -d out src\\main\\java\\com\\example\\App.java
                '''
            }
        }

        stage('Run App') {
            steps {
                bat "\"%JAVA%\" -cp out com.example.App"
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
