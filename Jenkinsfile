pipeline {
    agent any

    tools {
        // Define Maven tool by name as configured in Jenkins
        maven 'your_maven_installation_name'
    }

    stages {
        stage('Check Maven Version') {
            steps {
                script {
                    // Use 'tool' step to access the configured Maven tool
                    def mvnHome = tool name: 'your_maven_installation_name', type: 'maven'
                    // Execute the Maven command using the configured tool
                    def mvnVersion = sh(script: "${mvnHome}/bin/mvn --version", returnStdout: true).trim()
                    echo "Maven version: ${mvnVersion}"
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Define SonarQube scanner configuration
                    def scannerHome = tool name: 'Sonarqube', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    // Run SonarQube analysis using the configured scanner
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=demo-project -Dsonar.sources=src"
                }
            }
        }
    }
}



