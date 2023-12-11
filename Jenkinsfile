pipeline {
    agent any

    tools {
        // Define Maven tool by name as configured in Jenkins
        maven 'Maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Use 'withMaven' step to run Maven commands
                withMaven(maven: 'Maven) {
                    sh 'mvn clean install'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Use 'withMaven' to ensure the analysis uses the same Maven tool
                withMaven(maven: 'Maven') {
                    // Run SonarQube analysis
                    sh 'mvn sonar:sonar -Dsonar.projectKey=demo-project -Dsonar.sources=src'
                }
            }
        }
    }

    post {
        always {
            // Publish results to SonarQube dashboard
            script {
                // Retrieve Maven tool installation for SonarQube scanner
                def scannerHome = tool name: 'Maven', type: 'maven'
                // Run SonarQube scanner using the same Maven installation
                withMaven(maven: 'Maven') {
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=demo-project -Dsonar.sources=src"
                }
            }
        }
    }
}
