pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code repository
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Define SonarQube scanner configuration
                withSonarQubeEnv('Sonarqube') {
                    sh '''
                        # Assuming your project uses Maven for build
                        mvn clean install
                        mvn sonar:sonar -Dsonar.projectKey=demo-project -Dsonar.sources=src
                    '''
                }
            }
        }
    }

    post {
        always {
            // Publish results to SonarQube dashboard
            script {
                def scannerHome = tool name: 'Sonarqube-scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                withSonarQubeEnv('Sonarqube') {
                    // Publish results to SonarQube dashboard
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=your_project_key -Dsonar.sources=src"
                }
            }
        }
    }
}
