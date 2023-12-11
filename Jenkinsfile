pipeline {
    agent any

    // Define Maven tool by name as configured in Jenkins
    tools {
        maven 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                // Use 'withMaven' step to run Maven commands
                withMaven(maven: 'Maven') {
                    // Execute a simple Maven command, like 'mvn --version'
                    sh 'mvn --version'
                }
            }
        }
    }
}

