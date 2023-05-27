pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                sh 'cd app/ && npm install'
            }
        }
        stage('SonarQube Analysis') {
            def scannerHome = tool 'SonarQube';
            withSonarQubeEnv() {
            sh "${scannerHome}/bin/sonar-scanner"
            }
        }
    }
}
