pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'echo Building Java project...'
                sh 'javac -d build src/Cryptoalgo.java src/Main.java'
                sh 'echo Build successful'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Running JUnit tests for File-Encrypter...'
                sh 'curl -L -o junit-platform-console-standalone.jar https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.10.0/junit-platform-console-standalone-1.10.0.jar'
                sh 'java -jar junit-platform-console-standalone.jar --class-path build --scan-classpath'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploying...'
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
