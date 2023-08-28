pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {

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
                archiveArtifacts artifacts: 'build/libs/chaza-0.0.1-SNAPSHOT.jar', fingerprint: true
            }
        }
    }
}