pipeline {
    agent any

    tools {
        // Define Maven tool by name as configured in Jenkins
        maven 'Maven'
    }

    stages {
        stage('Check Maven Version') {
            steps {
                script {
                    // Use 'tool' step to access the configured Maven tool
                    def mvnHome = tool name: 'Maven', type: 'maven'
                    // Execute the Maven command using the configured tool
                    def mvnVersion = sh(script: "${mvnHome}/bin/mvn --version", returnStdout: true).trim()
                    echo "Maven version: ${mvnVersion}"
                }
            }
        }
    }
}



