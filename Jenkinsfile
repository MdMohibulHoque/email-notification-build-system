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
                echo 'Building Email Notification Build System...'
                bat 'mvn clean package'
            }
        }
    }

    post {

        success {
            emailext(
                subject: "✅ SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Hello Developer,

The build completed successfully.

Project Name : ${env.JOB_NAME}
Build Number : ${env.BUILD_NUMBER}
Build Status : ${currentBuild.currentResult}

Build URL:
${env.BUILD_URL}

Regards,
Jenkins CI
""",
                to: "zerin8135@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "❌ FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
Hello Developer,

The build has failed.

Project Name : ${env.JOB_NAME}
Build Number : ${env.BUILD_NUMBER}
Build Status : ${currentBuild.currentResult}

Please check the build log:

${env.BUILD_URL}

Regards,
Jenkins CI
""",
                to: "zerin8135@gmail.com"
            )
        }
    }
}