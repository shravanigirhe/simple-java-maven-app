pipeline {
    agent any

    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-21.0.10'
        JAVAC = '%JAVA_HOME%\\bin\\javac.exe'
        JAVA  = '%JAVA_HOME%\\bin\\java.exe'
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
                bat '''
                "%JAVA%" -cp out com.example.App
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Java 21 CI Pipeline SUCCESS (No Maven)'
        }
        failure {
            echo '❌ Java 21 CI Pipeline FAILED'
        }
    }
}
