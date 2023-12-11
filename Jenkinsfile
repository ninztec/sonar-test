node {
    stage('SCM') {
        checkout scm
    }

    stage('SonarQube Analysis') {
        def mvn = tool 'Maven';
        withSonarQubeEnv() {
            sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=demo-project -Dsonar.login=squ_fd0942453a2ac12b738874d67e1cc6865b0d8227"
        }
    }
}