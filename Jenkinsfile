pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', credentialsId: "LeeJin-token" ,url: 'https://github.com/dkwktm45/test-chaza2'

                script {
                    sh 'chmod +x ./gradlew'
                    sh './gradlew build -x test'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                script {
                    sh './gradlew test'
                }
            }
        }

        stage('Archive') {
            steps {
                echo 'Archiving the build artifacts...'
                archiveArtifacts artifacts: '/build/libs/chaza-0.0.1-SNAPSHOT.jar', fingerprint: true
            }
        }
    }
}