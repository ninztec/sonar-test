pipeline {
    agent any

    stages {
        stage('Check Maven Version') {
            steps {
                script {
                    // Execute a simple Maven command to display the version
                    def mvnVersion = sh(script: 'mvn --version', returnStdout: true).trim()
                    echo "Maven version: ${mvnVersion}"
                }
            }
        }
    }
}


