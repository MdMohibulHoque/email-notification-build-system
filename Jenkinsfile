pipeline {
    agent any

    tools {
        jdk 'JDK-25'
        maven 'Maven-3'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Maven Project...'
                bat 'mvn clean package'
            }
        }

    }

    post {

        success {
            echo 'Build completed successfully!'
        }

        failure {
            echo 'Build failed!'
        }

    }
}