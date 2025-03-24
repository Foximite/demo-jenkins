pipeline {
    agent any
    environment {
        PROJECT_NAME = 'demo-jenkins' // Replace with your project name
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Foximite/demo-jenkins.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Example for Java projects, you can change it based on your language
                    sh 'mvn clean install' // Replace with your build command
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Running tests
                    sh 'mvn test' // Replace with your test command
                }
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }
    post {
        success {
            echo 'Build and test successful!'
        }
        failure {
            echo 'Build failed. Check logs!'
        }
    }
}
