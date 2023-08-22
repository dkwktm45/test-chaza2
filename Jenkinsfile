pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', credentialsId: "LeeJin-token" ,url: 'https://github.com/dkwktm45/test-chaza'

                script {
                    // Use the Gradle Wrapper if your project uses Gradle

                    sh './gradlew build -x test'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                script {
                    // Use the Gradle Wrapper if your project uses Gradle
                    sh './gradlew test'
                }
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving the build artifacts...'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}